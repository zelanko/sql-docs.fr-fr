---
title: Publier et utiliser du code Python | Documents Microsoft
ms.custom: 
ms.date: 11/09/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: b060d27376b17709bd0f3fc8f39b8e01a6702e6b
ms.sourcegitcommit: ec5f7a945b9fff390422d5c4c138ca82194c3a3b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2017
---
# <a name="publish-and-consume-python-web-services"></a>Publier et consommer des services web de Python

Vous pouvez déployer une solution de Python de travail à un service web à l’aide de la fonctionnalité à l’Opérationnalisation dans Microsoft Machine Learning Server. Cette rubrique décrit les étapes pour publier, puis exécutez votre solution.

Le public cible de cet article est chercheurs de données qui souhaitent apprendre à publier du code Python ou des modèles en tant que services web hébergés dans Microsoft Machine Learning Server. Cet article explique comment les applications peuvent utiliser le code ou des modèles. Cet article suppose que vous maîtrisez Python.

> [!IMPORTANT]
>
> Cet exemple a été développé pour la version de Python qui est inclus avec Machine Learning Server (autonome) et utilise des fonctionnalités dans la version du serveur d’apprentissage Machine **9.1.0**.
 > 
 > Cliquez sur le lien suivant pour afficher le même exemple, republié à l’aide des bibliothèques dans Machine Learning Server plus récente. Consultez [déployer et gérer des services web dans Python](https://docs.microsoft.com/machine-learning-server/operationalize/python/how-to-deploy-manage-web-services).

**S’applique à : Microsoft R Server (autonome)**

## <a name="overview-of-workflow"></a>Vue d’ensemble du flux de travail

Le flux de travail à partir de la publication à l’utilisation d’un service web de Python peut être résumé comme suit :

1. Répondre à la [condition préalable](#prereq) de génération de la bibliothèque cliente de Python à partir du document d’API Swagger core.
2. Ajouter une logique d’authentification et d’en-tête à votre script Python.
3. Créer une session de Python, préparer l’environnement et créer une capture instantanée pour préserver l’environnement.
4. Le service web de publication et incorporer cette capture instantanée.
5. Tester le service web en temps dans votre session.
6. Pour gérer ces services.

![Flux de travail swagger](./media/data-scientist-python-workflow.png)

Cet article décrit chaque étape du flux de travail et inclut des exemples de code Python à l’aide du jeu de données iris.

## <a name="sample-code"></a>Exemple de code

Cet exemple de code suppose que vous avez rempli le [conditions préalables](#prereq) pour générer une bibliothèque cliente de Python à partir de ce Swagger fichier et que vous avez utilisé Autorest.

Après le bloc de code, vous trouverez une démonstration détaillée avec des descriptions plus détaillées le processus complet.

> [!IMPORTANT]
> Cet exemple utilise le `admin` de compte pour l’authentification. Toutefois, vous devez remplacer par les informations d’identification et [méthode d’authentification](#python-auth) configuré par votre administrateur.

```python
##################################################
##       IMPORT GENERATED CLIENT LIBRARY        ##
##################################################

# Import the generated client library. 

import deployrclient

# This example is intended for use with Microsoft R Server 9.0.1. 
# If you are using a newer version of Machine Learning Server, 
# use the mrs_server library instead.

##################################################
##              AUTHENTICATION                  ##
##################################################

#Using client library generated from Autorest
#Create client instance and point it at an R Server. 
#In this case, R Server is local.
client = deployrclient.DeployRClient("http://localhost:12800")
# To use ML Server, replace with mrs_server.MRSServer()

#Define the login request and provide credentials 
#Update values with the connection parameters from your admin
login_request = deployrclient.models.LoginRequest("<<your-username>>","<<your-password>>")

#Make a call to the /login API. 
#Store the returned an access token in a variable.
token_response = client.login(login_request)

#Add the returned access token to the headers variable.
headers = {"Authorization": "Bearer {0}".format(token_response.access_token)}

#Verify that the server is running.
#Remember to include `headers` in all requests!
status_response = client.status(headers) 
print(status_response.status_code)


##################################################
##        CREATE SESSION, MODEL, SNAPSHOT       ##
##################################################

#Since already logged in, create a Python session.
#Define session using name (`Session 1`) and `runtime_type="Python"`.
#Remember to specify the Python runtime type.
create_session_request = deployrclient.models.CreateSessionRequest("Session 1", runtime_type="Python")

#Make the call to start the session. 
#Remember to include headers in all method calls to the server.
#Returns a session ID.
response = client.create_session(create_session_request, headers) 
   
#Store the session ID in a variable called `session_id` 
#to be able to identify it later at execution time.
session_id = response.session_id

#Create model - Import SVM and datasets from the SciKit-Learn library
execute_request = deployrclient.models.ExecuteRequest("from sklearn import svm\nfrom sklearn import datasets")
execute_response = client.execute_code(session_id,execute_request, headers)
#Report if it was a success
execute_response.success
   
#Define the untrained Support Vector Classifier (SVC) object
#and the dataset to be preloaded.
execute_request = deployrclient.models.ExecuteRequest("clf=svm.SVC()\niris=datasets.load_iris()\nnames={0:'I. setosa',1:'I. versicolor',2:'I. virginica'}")
#Now, go create the object and preload Iris Dataset in R Server
execute_response = client.execute_code(session_id,execute_request, headers)
#Report if it was a success
execute_response.success
   
#Define two rows from the Iris Dataset as a sample for scoring
workspace_object = deployrclient.models.WorkspaceObject("species_1",[7,3.2,4.7,1.4])
workspace_object_2 = deployrclient.models.WorkspaceObject("species_2",[3,2.6,3,2.5])

#Define how to train the classifier model; what to predict; what to return
execute_request = deployrclient.models.ExecuteRequest(
    "clf.fit(iris.data, iris.target)\n"+
    "result=clf.predict(species_1)\n"+
    "other_result=clf.predict(species_2)",
    [workspace_object,workspace_object_2], #Input
    ["result", "other_result"]) #Output

#Now, go train that model on the Iris Dataset in R Server
execute_response = client.execute_code(session_id,execute_request, headers)

#If successful, print name and result of each output parameter. Else, print error.
if(execute_response.success):
    for result in execute_response.output_parameters:
        print("{0}: {1}".format(result.name,result.value))
else:
    print (execute_response.error_message)

#Create a snapshot of the current session
response = client.create_snapshot(session_id, deployrclient.models.CreateSnapshotRequest("Iris Snapshot"), headers)
#Return the snapshot ID for reference when you publish later.
response.snapshot_id
#If you forget the ID, list snapshots to get the ID again.
for snapshot in client.list_snapshots(headers):
    print(snapshot)

##################################################
##        PUBLISH AS A SERVICE IN PYTHON        ##
##################################################

#Define a web service that determines the iris species by scoring 
#a vector of sepal length and width, petal length and width

#Set `flower_data` for the sepal and petal length and width
flower_data = deployrclient.models.ParameterDefinition(name = "flower_data", type = "vector")
#Set `iris_species` for the species of iris
iris_species = deployrclient.models.ParameterDefinition(name = "iris_species", type = "vector")

#Define the publish request for the web service and its arguments.
#Specify the code, inputs, outputs, and snapshot.
#Don't forget to set runtime_type="Python"`.
publish_request = deployrclient.models.PublishWebServiceRequest(
       code = "iris_species = [names[x] for x in clf.predict(flower_data)]", 
       input_parameter_definitions = [flower_data], 
       output_parameter_definitions = [iris_species],
       runtime_type = "Python",
       snapshot_id = response.snapshot_id)

#Publish the service using the specified name (iris), version (V1.0)
client.publish_web_service_version("Iris", "V1.0", publish_request, headers)

##################################################
##           CONSUME SERVICE IN PYTHON          ##
##################################################

# Inspect holdings and metadata for service Iris V1.0.
for service in client.get_web_service_version("Iris","V1.0", headers):
    #print service metadata (description, who published,...)
    print(service)
    #Print input and output parameters as defined in service definition object
    print("Input Parameters: {0}".format([str(parameter) for parameter in service.input_parameter_definitions]))
    print("Output Parameters: {0}".format([str(parameter) for parameter in service.output_parameter_definitions]))

#Import the requests library to make requests on the server
import requests
#Import the JSON library to use for pretty printing of json responses
import json

#Create a requests `Session` object.
s = requests.Session()

#Record the R Server endpoint URL hosting the web services you created before
url = "http://localhost:12800"

#Give the request.Session object the authentication headers 
#so you don't have to repeat it with each request.
s.headers = headers

#Retrieve the service-specific swagger file using the requests library.
swagger_resp = s.get(url+"/api/Iris/V1.0/swagger.json")

#Either, download service-specific swagger file using the json library.
with open('iris_swagger.json','w') as f:
   (json.dump(client.get_web_service_swagger("Iris","V1.0",headers),f, indent = 1))

#Or, print just what you need from the Swagger file, 
#such as the routing paths for the endpoints to be consumed.
print(json.dumps(swagger_resp.json()["paths"], indent = 1, sort_keys = True))

#Or, print input and output parameters as defined in the Swagger.io format
print("Input")
print(json.dumps(swagger_resp.json()["definitions"]["InputParameters"], indent = 1, sort_keys = True))
print("Output")
print(json.dumps(swagger_resp.json()["definitions"]["WebServiceResult"], indent = 1, sort_keys = True))

#Make the request to consume the service using these flower_data inputs
resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[7,3.2,4.7,1.4]})
#Print the output
print(json.dumps(resp.json(), indent = 1, sort_keys = True))

#Use input from another Iris species.
resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[3,2.6,3,2.5]})
print(json.dumps(resp.json(), indent = 1, sort_keys = True))

#Use input from another Iris species.
resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[5.1,3.5,1.4,.2]})
print(json.dumps(resp.json(), indent = 1, sort_keys = True))

##################################################
##          MANAGE SERVICES IN PYTHON           ##
##################################################

#Define what needs to be updated. Here we add a description.
#Be sure to specify the runtime_type again.
update_request = deployrclient.models.PublishWebServiceRequest(
    description = "Determines iris species using length and width of sepal and petal", runtime_type = "Python")
#Now update it by specifying the service name and version number
client.patch_web_service_version("Iris", "V1.0", update_request, headers)

#Or, publish another version of the web service, but this time 
#the service returns the species as a string instead of list of strings.
flower_data = deployrclient.models.ParameterDefinition(name = "flower_data", type = "vector")
iris_species = deployrclient.models.ParameterDefinition(name = "iris_species", type = "string")
 
#Define the publish request for the service and its arguments.
#Specify the changed code, inputs, outputs, and snapshot.
#Don't forget to set runtime_type="Python"`.
publish_request = deployrclient.models.PublishWebServiceRequest(
    code = "iris_species = [names[x] for x in clf.predict(flower_data)][0]",
    description = "Determines the species of iris, based on Sepal Length, Sepal Width, Petal Length and Petal Width",
    input_parameter_definitions = [flower_data],
    output_parameter_definitions = [iris_species],
    runtime_type = "Python",
    snapshot_id = response.snapshot_id)
 
#Now, publish the service with version (V2.0)
client.publish_web_service_version("Iris", "V2.0", publish_request, headers)
 
#Make request to consume service using these flower_data inputs; print output
resp = s.post(url+"/api/Iris/V2.0",json={"flower_data":[5.1,3.5,1.4,.2]})
print(json.dumps(resp.json(), indent = 1, sort_keys = True))

#Return the list of all existing web services.
for service in client.get_all_web_services(headers):
    #print the service information
    print(service)
    #Print each input and output parameter
    print("Input Parameters: {0}".format([str(parameter) for parameter in service.input_parameter_definitions]))
    print("Output Parameters: {0}".format([str(parameter) for parameter in service.output_parameter_definitions]))

#Delete the second version we just published.
client.delete_web_service_version("Iris","V2.0",headers)
```

## <a name="walkthrough"></a>Procédure pas à pas

Cette section décrit comment le code fonctionne plus en détail.


### <a name="prereq"></a>Étape 1. Créer des bibliothèques de client requis

Avant de commencer votre Python code et les modèles au moyen d’ordinateur Microsoft Learning le serveur de publication, vous devez générer une bibliothèque cliente à l’aide du document de Swagger fourni pour cette version.

1. Installer un générateur de code Swagger sur votre ordinateur local et vous familiariser avec elle. Vous allez l’utiliser pour générer des bibliothèques API clientes de Python. Outils courants incluent [Azure AutoRest](https://github.com/Azure/autorest) (nécessite Node.js) et [Codegen de Swagger](https://github.com/swagger-api/swagger-codegen). 

2. Téléchargez le fichier Swagger contenant les API principales pour votre version du serveur de Machine Learning. Ce fichier contient un modèle Swagger de définition de la liste de ressources REST et les opérations qui peuvent être appelées sur ces ressources. Vous pouvez trouver ce fichier sous `https://microsoft.github.io/deployr-api-docs/swagger/<version>/rserver-swagger-<version>.json`, où `<version>` est le numéro de version de R Server à 3 chiffres. 

   Par exemple, pour R Server 9.1 vous devez télécharger à partir : https://microsoft.github.io/deployr-api-docs/9.1.0/swagger/rserver-swagger-9.1.0.json

3. Générer la bibliothèque cliente statiquement générée en passant le `rserver-swagger-<version>.json` de fichier pour le Générateur de code Swagger et spécification de la langue que vous souhaitez. Dans ce cas, vous devez spécifier les Python.  

    Par exemple, si vous utilisez AutoRest pour générer une bibliothèque cliente de Python, elle peut ressembler à ceci, où le nombre de chiffres 3 représente le numéro de version de R Server :
    
    `AutoRest.exe -Input rserver-swagger-9.1.0.json -CodeGenerator Python  -OutputDirectory C:\Users\rserver-user\Documents\Python`

4. Vous pouvez également fournir certains en-têtes personnalisés et apporter d’autres modifications avant d’utiliser le client généré stub de la bibliothèque. Consultez le [Interface de ligne de commande](https://github.com/Azure/autorest/blob/master/docs/user/cli.md) documentation sur GitHub pour plus d’informations concernant les différentes options de configuration et les préférences, telles que la modification du nom de l’espace de noms.
   
5. Explorer la principale bibliothèque de client pour afficher les appels API que vous pouvez apporter. 

    Dans notre exemple, Autorest généré certains répertoires et fichiers de la bibliothèque cliente de Python sur votre système local. Par défaut, l’espace de noms (ou un répertoire) sont `deployrclient` et peut ressembler à ceci :
   
   ![Chemin de sortie Autorest](./media/data-scientist-python-autorest.png)

    Pour cet espace de noms par défaut, la bibliothèque cliente lui-même est appelée `deploy_rclient.py`. Si vous ouvrez ce fichier dans votre IDE tel que Visual Studio, vous voyez quelque chose comme ceci :
   
   ![Bibliothèque cliente de Python](./media/data-scientist-python-client-library.png)


### <a name="step-2-add-authentication-and-header-logic"></a>Étape 2. Ajouter une logique d’authentification et d’en-tête

N’oubliez pas que toutes les API requièrent l’authentification ; Par conséquent, tous les utilisateurs doivent s’authentifier lors d’une API à appeler à l’aide de la `POST /login` API ou via Azure Active Directory (AAD). 

Pour simplifier ce processus, les jetons d’accès de support sont émis afin que les utilisateurs pas besoin de fournir leurs informations d’identification pour chaque appel.  Ce jeton de support est un jeton de sécurité léger qui octroie l’accès « support » à une ressource protégée : dans ce cas, les API du serveur Machine Learning. Après qu’un utilisateur a été authentifié, l’application doit valider le jeton de support de l’utilisateur pour vous assurer que l’authentification a réussi pour les parties concernées. Pour en savoir plus sur la gestion de ces jetons, consultez [jetons d’accès de sécurité](https://msdn.microsoft.com/microsoft-r/operationalize/security-access-tokens).

Avant de vous interagissez avec l’API de base, tout d’abord s’authentifier, obtenir l’accès au support de jeton à l’aide de la [méthode d’authentification](https://msdn.microsoft.com/microsoft-r/operationalize/security-authentication) configuré par votre administrateur et l’inclure dans chaque en-tête pour chaque demande suivante :

1. Commencez par l’importation de la bibliothèque cliente pour le rendre accessible à partir de votre Python préféré éditeur de code, tels que Notebook, Visual Studio, Visual Studio Code ou notebooks.

   Spécifiez le répertoire parent de la bibliothèque cliente. Dans notre exemple, la bibliothèque de client généré Autorest est sous `C:\Users\rserver-user\Documents\Python\deployrclient`:

   ```python
   # Import the generated client library
   import deployrclient
   ```

2. Ajouter la logique d’authentification à votre application pour définir une connexion à partir de votre ordinateur local à serveur de Machine Learning, fournir des informations d’identification, le jeton d’accès de capture, ajouter ce jeton à l’en-tête. Vous utilisez ensuite cet en-tête pour toutes les demandes ultérieures.  Utilisez la méthode d’authentification définie par l’administrateur : compte d’administrateur de base, Active Directory LDAP (AD/LDAP) ou Azure Active Directory (AAD).

   **AD/LDAP ou `admin` l’authentification de compte**

   Appelez le `POST /login` API pour s’authentifier. Passez le `username` et `password` pour l’administrateur local, ou si Active Directory est activée, passer les informations de compte LDAP. À son tour, Machine Learning Server émet un jeton de support ou d’y accéder. Une fois authentifié, l’utilisateur n’a plus besoin fournir des informations d’identification à nouveau, tant que le jeton est toujours valide et un en-tête est envoyé avec chaque demande. Si vous ne connaissez pas vos paramètres de connexion, contactez votre administrateur.

   ```python
   #Using client library generated from Autorest
   #Create client instance and point it at an R Server. 
   #In this case, R Server is local.
   client = deployrclient.DeployRClient("http://localhost:12800")
   
   #Define the login request and provide credentials. 
   #Update values with the connection parameters from your admin.
   login_request = deployrclient.models.LoginRequest("<<your-username>>","<<your-password>>")
   #Make a call to the /login API. 
   #Store the returned an access token in a variable.
   token_response = client.login(login_request)
   ```

   **Authentification Azure Active Directory (AAD)**

   Passer les informations d’identification AAD, autorité et ID de client. À son tour, AAD émet le [jeton d’accès de support](https://msdn.microsoft.com/microsoft-r/operationalize/security-access-tokens). Une fois authentifié, l’utilisateur n’a plus besoin fournir des informations d’identification à nouveau, tant que le jeton est toujours valide et un en-tête est envoyé avec chaque demande. Si vous ne connaissez pas vos paramètres de connexion, contactez votre administrateur.

   ```python
   #Import the AAD authentication library
   import adal
   
   #Define the login request and provide credentials. 
   #Use the AAD connection parameters provided by your admin.
   url = "http://localhost:12800"
   authuri = https://login.windows.net,
   tenantid = "<<AAD_DOMAIN>>", 
   clientid = "<<NATIVE_APP_CLIENT_ID>>", 
   resource = "<<WEB_APP_CLIENT_ID>>", 
   
   #Acquire authentication token using AAD Device Code Login
   context = adal.AuthenticationContext(authuri+'/'+tenantid, api_version=None)
   code = context.acquire_user_code(resource, clientid)
   print(code['message'])
   token = context.acquire_token_with_device_code(resource, code, clientid)
   #The authentication code returned must be entered at https://aka.ms/devicelogin 
   ```     

3. Ajouter le `Bearer` accéder au jeton et vérifiez que la Machine Learning Server est en cours d’exécution.  Ce jeton a été retourné lors de l’authentification et **doit être inclus dans chaque en-tête de demande ultérieure**. Cet exemple utilise une bibliothèque cliente générée par Autorest.

   > [!IMPORTANT]
   > Chaque appel d’API doit être authentifiée. Par conséquent, n’oubliez pas d’inclure les en-têtes des jetons à chaque demande.

   ```python
   #Add the returned access token to the headers variable.
   headers = {"Authorization": "Bearer {0}".format(token_response.access_token)}
   
   #Verify that the server is running.
   #Remember to include `headers` in every request!
   status_response = client.status(headers) 
   print(status_response.status_code)
   ```

### <a name="step-3-prepare-session-and-code"></a>Étape 3. Préparer la session et le code

Après l’authentification, vous pouvez démarrer une session de Python et créer un modèle pour la publication des versions ultérieures. Vous pouvez inclure n’importe quel code Python ou des modèles dans un service web. Une fois que vous avez configuré votre environnement de session, vous pouvez l’enregistrer même en tant qu’instantané, ce qui vous pouvez recharger votre session comme vous l’aviez avant. 

> [!IMPORTANT]
> N’oubliez pas d’inclure `headers` dans chaque demande.

1. Créer une session de Python sur R Server. Veillez à spécifier un nom et le langage Python (`runtime_type="Python"`).  Si vous ne définissez pas le type de runtime pour Python, la valeur par défaut R.

   Il s’agit d’une continuation de l’exemple à l’aide de la bibliothèque de client générée par Autorest :

   ```python
   #Since already logged in, create a Python session.
   #Define session using name (`Session 1`) and `runtime_type="Python"`.
   #Remember to specify the Python runtime type.
   create_session_request = deployrclient.models.CreateSessionRequest("Session 1", runtime_type="Python")
   
   #Make the call to start the session. 
   #Remember to include headers in every method call to the server.
   #Returns a session ID.
   response = client.create_session(create_session_request, headers) 
   
   #Store the session ID in a variable called `session_id` 
   #to be able to identify it later at execution time.
   session_id = response.session_id
   ```

2. Créer ou appeler un modèle dans Python que vous allez publier en tant que service web

   Dans cet exemple, nous former un modèle de machines (SVM)-en savoir plus SciKit prise en charge de vecteur sur le Iris Dataset sur une instance distante du serveur de Machine Learning.  Ce jeu de données est disponible à partir de la [scikit-en savoir plus du site](http://scikit-learn.org/stable/auto_examples/datasets/plot_iris_dataset.html).

   ```python
   #Import SVM and datasets from the SciKit-Learn library
   execute_request = deployrclient.models.ExecuteRequest("from sklearn import svm\nfrom sklearn import datasets")
   execute_response = client.execute_code(session_id,execute_request, headers)
   #Report if it was a success
   execute_response.success
   
   #Define the untrained Support Vector Classifier (SVC) object
   #and the dataset to be preloaded.
   execute_request = deployrclient.models.ExecuteRequest("clf=svm.SVC()\niris=datasets.load_iris()\nnames={0:'I. setosa',1:'I. versicolor',2:'I. virginica'}")
   #Now, go create the object and preload Iris Dataset in R Server
   execute_response = client.execute_code(session_id,execute_request, headers)
   #Report if it was a success
   execute_response.success
   
   #Define two rows from the Iris Dataset as a sample for scoring
   workspace_object = deployrclient.models.WorkspaceObject("species_1",[7,3.2,4.7,1.4])
   workspace_object_2 = deployrclient.models.WorkspaceObject("species_2",[3,2.6,3,2.5])

   #Define how to train the classifier model; what to predict; what to return
   execute_request = deployrclient.models.ExecuteRequest(
       "clf.fit(iris.data, iris.target)\n"+
       "result=clf.predict(species_1)\n"+
       "other_result=clf.predict(species_2)",
       [workspace_object,workspace_object_2], #Input
       ["result", "other_result"]) #Output

   #Now, go train that model on the Iris Dataset in R Server
   execute_response = client.execute_code(session_id,execute_request, headers)

   #If successful, print name and result of each output parameter. Else, print error.
   if(execute_response.success):
       for result in execute_response.output_parameters:
           print("{0}: {1}".format(result.name,result.value))
   else:
       print (execute_response.error_message)
   ```

3. Créer un instantané de cette Python session afin de cet environnement peut être enregistré dans le service web et reproduit consomment le temps. Les instantanés sont utiles lorsque vous avez besoin d’un environnement préparé qui inclut certaines bibliothèques, les objets, les modèles, les fichiers et les artefacts. Instantanés d’enregistrer l’espace de travail entier et le répertoire de travail. Toutefois, lors de la publication, vous pouvez utiliser uniquement les instantanés que vous avez créée.

   ```python
   #Create a snapshot of the current session.
   response = client.create_snapshot(session_id, deployrclient.models.CreateSnapshotRequest("Iris Snapshot"), headers)
   
   #Return the snapshot ID for reference when you publish later.
   response.snapshot_id
   
   #If you forget the ID, list snapshots to get the ID again.
   for snapshot in client.list_snapshots(headers):
       print(snapshot)
   ```

  > [!NOTE] 
   > Alors que les instantanés peuvent également être utilisés lors de la publication d’un service web pour les dépendances de l’environnement, il peut avoir un impact sur les performances de la durée de la consommation.  Pour des performances optimales, réfléchissez bien avant de la taille de l’instantané et vous assurer que seuls les objets d’espace de travail vous avez besoin et purger le reste. Dans une session, vous pouvez utiliser Python `del` fonction ou [le `deleteWorkspaceObject` de demande d’API](https://microsoft.github.io/deployr-api-docs/#delete-workspace-object) pour supprimer les objets inutiles. 

### <a name="step-4-publish-the-model"></a>Étape 4. Publier le modèle 

Une fois que votre bibliothèque cliente a été généré et que vous avez créé la logique d’authentification dans votre application, vous pouvez interagir avec l’API pour créer une session de Python, créer un modèle et puis publier un service web à l’aide de ce modèle de base.

Certains points à retenir :

+ Vous devez être authentifié avant d’effectuer des appels d’API. Par conséquent, inclure `headers` dans toutes les demandes.
+ Pour vous assurer que le service web est enregistré comme un service de Python, veillez à spécifier `runtime_type="Python"`. Si vous ne définissez pas le type de runtime pour Python, la valeur par défaut R.
+ Calcul de score nécessite un vecteur de longueur des sépales, la largeur des sépales, longueur de pétale et la largeur

Le code suivant permet de publier le modèle SVM comme service web Python. Ce service web génère une catégorie prédite en fonction des valeurs qui lui est passés.

```python
   #Set `flower_data` for the sepal and petal length and width
   flower_data = deployrclient.models.ParameterDefinition(name = "flower_data", type = "vector")
   #Set `iris_species` for the species of iris
   iris_species = deployrclient.models.ParameterDefinition(name = "iris_species", type = "vector")
   
   #Define the publish request for the web service and its arguments.
   #Specify the code, inputs, outputs, and snapshot.
   #Don't forget to set runtime_type="Python"`.
   publish_request = deployrclient.models.PublishWebServiceRequest(
       code = "iris_species = [names[x] for x in clf.predict(flower_data)]", 
       input_parameter_definitions = [flower_data], 
       output_parameter_definitions = [iris_species],
       runtime_type = "Python",
       snapshot_id = response.snapshot_id)

   #Publish the service using the specified name (iris), version (V1.0)
   client.publish_web_service_version("Iris", "V1.0", publish_request, headers)
```

### <a name="step-5-consume-the-web-service"></a>Étape 5. Consommer le service web

Cette section montre comment consommer le service dans la même session que celui sur lequel il a été créé.

1. Dans la même session, obtenir les métadonnées et les exploitations du service pour le service.

   ```python
   # Inspect holdings and metadata for service Iris V1.0.
   for service in client.get_web_service_version("Iris","V1.0", headers):
       #print service metadata (description, who published,...)
       print(service)
       #Print input and output parameters as defined in service definition object
       print("Input Parameters: {0}".format([str(parameter) for parameter in service.input_parameter_definitions]))
       print("Output Parameters: {0}".format([str(parameter) for parameter in service.output_parameter_definitions]))
   ```

2. Examiner les exploitations du service et préparer le consommer. 
   ```python
   #Import the requests library to make requests on the server
   import requests
   #Import the JSON library to use for pretty printing of json responses
   import json

   #Create a requests `Session` object.
   s = requests.Session()

   #Record the R Server endpoint URL hosting the web services you created
   url = "http://localhost:12800"

   #Include the request.Session object in the authentication headers.
   #By doing so, you don't need to repeat it with each request.
   s.headers = headers

   # Retrieve the service-specific Swagger file using the requests library.
   swagger_resp = s.get(url+"/api/Iris/V1.0/swagger.json")

   #You can download a service-specific Swagger file using the json library.
   with open('iris_swagger.json','w') as f:
      (json.dump(client.get_web_service_swagger("Iris","V1.0",headers),f, indent = 1))

   #Or, you can print just what you need from the Swagger file. 
   #This example gets the routing paths for the endpoints to be consumed.
   print(json.dumps(swagger_resp.json()["paths"], indent = 1, sort_keys = True))

   #You can also print input and output parameters as defined in the Swagger.io format
   print("Input")
   print(json.dumps(swagger_resp.json()["definitions"]["InputParameters"], indent = 1, sort_keys = True))
   print("Output")
   print(json.dumps(swagger_resp.json()["definitions"]["WebServiceResult"], indent = 1, sort_keys = True))
   ```

3. Consommer le service, vous devez fournir certaines d’entrée et de mise en route d’espèces Iris. 
   ```python
   #Make the request to consume the service using these flower_data inputs
   resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[7,3.2,4.7,1.4]})
   #Print the output
   print(json.dumps(resp.json(), indent = 1, sort_keys = True))

   ##Use input from another Iris species.
   resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[3,2.6,3,2.5]})
   print(json.dumps(resp.json(), indent = 1, sort_keys = True))

   ##Use input from another Iris species.
   resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[5.1,3.5,1.4,.2]})
   print(json.dumps(resp.json(), indent = 1, sort_keys = True))
   ```

## <a name="managing-the-services"></a>Gestion des services

Maintenant que vous avez créé un service web, vous pouvez mettre à jour, supprimer ou republier ce service. Vous pouvez également répertorier tous les services web qui sont hébergés à l’aide de R Server (ou serveur de Machine Learning).

### <a name="update-a-web-service"></a>Mettre à jour un service web

 Dans cet exemple, nous mettre à jour le service pour ajouter une description utile pour les personnes qui peuvent utiliser ce service.

```python
#Define what needs to be updated. Here we add a description.
#Be sure to specify the runtime_type again.
update_request = deployrclient.models.PublishWebServiceRequest(
    description = "Determines iris species using length and width of sepal and petal", runtime_type = "Python")
#Now update it by specifying the service name and version number
client.patch_web_service_version("Iris", "V1.0", update_request, headers)
```

Vous pouvez mettre à jour un service web pour modifier le code, modèle, description, les entrées, sorties et bien plus encore.

### <a name="publish-another-version"></a>Une autre version de publication

Dans cet exemple, le service retourne maintenant espèces Iris sous forme de chaîne au lieu d’une liste de chaînes.

```python
#Publish another version of the web service, but this time 
#the service returns the species as a string instead of list of strings.
flower_data = deployrclient.models.ParameterDefinition(name = "flower_data", type = "vector")
iris_species = deployrclient.models.ParameterDefinition(name = "iris_species", type = "string")
 
#Define the publish request for the service and its arguments.
#Specify the changed code, inputs, outputs, and snapshot.
#Don't forget to set runtime_type="Python"`.
publish_request = deployrclient.models.PublishWebServiceRequest(
    code = "iris_species = [names[x] for x in clf.predict(flower_data)][0]",
    description = "Determines the species of iris, based on Sepal Length, Sepal Width, Petal Length and Petal Width",
    input_parameter_definitions = [flower_data],
    output_parameter_definitions = [iris_species],
    runtime_type = "Python",
    snapshot_id = response.snapshot_id)
 
#Now, publish the service with version (V2.0)
client.publish_web_service_version("Iris", "V2.0", publish_request, headers)
 
#Make request to consume service using these flower_data inputs; print output
resp = s.post(url+"/api/Iris/V2.0",json={"flower_data":[5.1,3.5,1.4,.2]})
print(json.dumps(resp.json(), indent = 1, sort_keys = True))
```

Ce modèle vous permet de publier plusieurs versions du même service web. 

### <a name="list-services"></a>Liste des services

Cet exemple obtient une liste de tous les services web, y compris ceux créés par d’autres utilisateurs ou dans différentes langues.

```python
#Return the list of all existing web services.
for service in client.get_all_web_services(headers):
    #print the service information
    print(service)
    #Print each input and output parameter
    print("Input Parameters: {0}".format([str(parameter) for parameter in service.input_parameter_definitions]))
    print("Output Parameters: {0}".format([str(parameter) for parameter in service.output_parameter_definitions]))
``` 

### <a name="delete-services"></a>Supprimer des services

Dans cet exemple, nous supprimons la deuxième version de service web que nous vient d’être publiés.

```python
#Delete the second version we just published.
client.delete_web_service_version("Iris","V2.0",headers)
```

Vous pouvez supprimer n’importe quel service que vous avez créé. Vous pouvez supprimer les services d’autres uniquement si vous êtes affecté à un rôle qui dispose des autorisations appropriées.