---
title: "Dépannage de SQL Server Integration Services (SSIS) de montée en charge | Documents Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 41bb853dd08591596f6f5baa918e174d0c26a6b5
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="troubleshooting-scale-out"></a>Résolution des problèmes de montée en puissance parallèle

SSIS monter en charge implique communtication entre SSISDB, le service de mise à l’échelle des principales et de service de mise à l’échelle des processus de travail. Parfois, la communication est interrompue en raison d’erreurs de configuration, un manque d’autorisations d’accès et d’autres raisons. Ce document vous aide à dépanner votre configuration monter en charge.

Pour étudier les problèmes que vous rencontrez, suivez les étapes ci-dessous un par un jusqu'à ce que votre problème est résolu.

### <a name="symptoms"></a>**Symptômes** 
Échelle Out principale ne peut pas se connecter à SSISDB. 

Propriétés principales ne peut pas afficher dans l’échelle des Manager.

Propriétés principales ne sont pas remplies [SSISDB]. [catalogue]. [master_properties]

### <a name="solution"></a>**Solution**
Étape 1 : Vérifier si l’option monter en charge est activée.

Avec le bouton droit **SSISDB** nœud dans l’Explorateur d’objets de SSMS et vérification **monter en charge la fonctionnalité est activée**.

![Est monter en charge est-il activé](media\isenabled.PNG)

Si la valeur de propriété est False, activez monter en charge en appelant la procédure stockée [SSISDB]. [catalogue]. [enable_scaleout].

Étape 2 : Vérifiez si le nom Sql Server spécifié dans le fichier de configuration de mise à l’échelle des principale est correct et redémarrez le service de mise à l’échelle des principales.

### <a name="symptoms"></a>**Symptômes** 
Montée en puissance des processus de travail ne peut pas se connecter à l’échelle des principales

Montée en puissance des processus de travail n’apparaît pas après l’avoir ajoutée dans l’échelle des Manager

Montée en puissance des processus de travail n’affiche pas dans [SSISDB]. [catalogue]. [worker_agents]

Service de mise à l’échelle des processus de travail est en cours d’exécution, tandis que la montée en puissance des processus de travail est hors connexion

### <a name="solutions"></a>**Solutions** 
Vérifiez les messages d’erreur dans le journal de service de mise à l’échelle des processus de travail sous \<pilote\>: \Users\\*[compte de service de travail en cours d’exécution]*\AppData\Local\SSIS\Cluster\Agent.

**Cas** 

System.ServiceModel.EndpointNotFoundException : Aucun point de terminaison à l’écoute sur https:// produite*[NomOrdinateur] : [Port]*/ClusterManagement/ pouvant accepter le message.

Étape 1 : Vérifiez si le numéro de port spécifié dans le fichier de configuration de service de mise à l’échelle des principale est correct et redémarrez le service de mise à l’échelle des principales. 

Étape 2 : Vérifiez si le point de terminaison principal spécifié dans la configuration de service de mise à l’échelle des processus de travail est correct et redémarrez le service de mise à l’échelle des processus de travail.

Étape 3 : Vérifier si le port de pare-feu est ouvert sur le nœud de l’échelle des principales.

Étape 4 : Résoudre les problèmes de connexion entre les nœuds de l’échelle des principales et montée en puissance des processus de travail.

**Cas**

System.ServiceModel.Security.SecurityNegotiationException : N’a pas pu établir la relation d’approbation pour le canal sécurisé SSL/TLS avec l’autorité '*[nom_ordinateur] : [Port]*». ---> System.Net.WebException : la connexion sous-jacente a été fermée : Impossible d’établir une relation d’approbation pour le canal sécurisé SSL/TLS. ---> System.Security.Authentication.AuthenticationException : le certificat distant n’est pas valide selon la procédure de validation.

Étape 1 : Installation échelle Out Master de certificat au magasin de certificats racine de l’ordinateur local sur le nœud de la montée en puissance des processus de travail si ce n’est pas encore installé et redémarrez le service de mise à l’échelle des processus de travail.

Étape 2 : Vérifier si le nom d’hôte dans le point de terminaison principal est inclus dans le certificat de noms communs d’échelle Out principal. Si ce n’est pas le cas, réinitialisez le point de terminaison principal dans le fichier de configuration de montée en puissance des processus de travail et redémarrez le service de mise à l’échelle des processus de travail. 

> [!Note]
> Si elle n’est pas possible de modifier le nom d’hôte du point de terminaison master en raison des paramètres DNS, vous devez modifier le certificat de l’échelle des principales. Consultez [les certificats dans SSIS monter en charge](deal-with-certificates-in-ssis-scale-out.md).

Étape 3 : Vérifier si l’empreinte numérique du principal spécifié dans la configuration de la montée en puissance des processus de travail correspond à l’empreinte numérique du certificat de mise à l’échelle des principales. 

**Cas**

System.ServiceModel.Security.SecurityNegotiationException : Impossible d’établir un canal sécurisé pour SSL/TLS avec l’autorité '*[nom_ordinateur] : [Port]*». ---> System.Net.WebException : la demande a été abandonnée : a pas pu créer un canal sécurisé SSL/TLS.

Étape 1 : Vérifier si le compte exécutant le service de mise à l’échelle des processus de travail a accès au certificat de montée en puissance des processus de travail par la commande ci-dessous.

```dos
winhttpcertcfg.exe -l -c LOCAL_MACHINE\MY -s {CN of the worker certificate}
```

Si le compte n’a pas accès, accordez à la commande ci-dessous et redémarrez le service de mise à l’échelle des processus de travail.

```dos
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s {CN of the worker certificate} -a {the account running Scale Out Worker service}
```

**Cas**

System.ServiceModel.Security.MessageSecurityException : La requête HTTP a été interdite avec le schéma d’authentification client « Anonyme ». ---> System.Net.WebException : le serveur distant a retourné une erreur : (403) interdit.

Étape 1 : Installation mise à l’échelle des traitement de certificat au magasin de certificats racine de l’ordinateur local sur le nœud de l’échelle des principales si ce n’est pas encore installé et redémarrer le service de mise à l’échelle des processus de travail.

Étape 2 : Nettoyer les certificats inutiles dans le magasin de certificats racine de l’ordinateur local sur le nœud de l’échelle des principales.

Étape 3 : Configurer Schannel pour ne plus envoyer la liste des autorités de certification racine de confiance pendant le processus de négociation TLS/SSL, en ajoutant l’entrée de Registre ci-dessous sur le nœud de l’échelle des principales.

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL

Nom de la valeur : SendTrustedIssuerList 

Valeur de type : REG_DWORD 

Données de la valeur : 0 (faux)

**Cas**

System.ServiceModel.CommunicationException : Une erreur s’est produite lors de la requête HTTP à https://*[nom_ordinateur] : [Port]*  /ClusterManagement /. Cela peut être dû au fait que le certificat de serveur n’est pas configuré correctement avec HTTP. SYS dans le cas HTTPS. Cela peut également être dû à une incompatibilité de la liaison de sécurité entre le client et le serveur. 

Étape 1 : Vérifier si Scale Out Master certificat est lié au port de point de terminaison principal correctement sur le nœud principal avec la commande ci-dessous. Vérifiez si le hachage de certificat affiché est mis en correspondance avec l’empreinte numérique du certificat de Scale Out Master.

```dos
netsh http show sslcert ipport=0.0.0.0:{Master port}
```

Si la liaison n’est pas correcte, réinitialiser avec les commandes suivantes et redémarrez le service de mise à l’échelle des processus de travail.

```dos
netsh http delete sslcert ipport=0.0.0.0:{Master port}
netsh http add sslcert ipport=0.0.0.0:{Master port} certhash={Master certificate thumbprint} certstorename=Root appid={random guid}
```

### <a name="symptoms"></a>**Symptômes**
L’exécution de monter en charge ne démarre pas.

### <a name="solution"></a>**Solution**

Vérifiez l’état des ordinateurs que vous avez sélectionné pour exécuter le package dans [SSISDB]. [catalogue]. [worker_agents]. Au moins un travail doit être en ligne et activé.

### <a name="symptoms"></a>**Symptômes** 
Exécution des packages, mais aucun message n’est connecté.

### <a name="solution"></a>**Solution**

Vérifiez si l’authentification SQL Server est autorisée par le serveur Sql Server qui héberge SSISDB.

> [!Note]  
> Si vous avez modifié le compte pour la journalisation de monter en charge, consultez [modifier le compte pour la montée en puissance hors connexion](change-logdb-account.md) et vérifiez la chaîne de connexion utilisée pour la journalisation.

### <a name="symptoms"></a>**Symptômes**
Les messages d’erreur dans le rapport d’exécution de package ne sont pas suffisantes pour le dépannage.

### <a name="solution"></a>**Solution**
Plusieurs journaux d’exécution peuvent être trouvées sous TasksRootFolder configuré dans WorkerSettings.config. Par défaut, il est \<pilote\>: \Users\\*[compte]*\AppData\Local\SSIS\ScaleOut\Tasks. Le *[compte]* est le compte de service de mise à l’échelle des processus de travail en cours d’exécution avec SSISScaleOutWorker140 par défaut.

Pour localiser le journal pour l’exécution du package avec *[id d’exécution]*, exécutez la commande T-SQL ci-dessous pour obtenir le *[ID de tâche :]*. Ensuite, recherchez le sous-dossier nommé avec *[ID de tâche :]* sous TasksRootFolder.<sup> 1<sup>

```sql
SELECT [TaskId]
FROM [SSISDB].[internal].[tasks] tasks, [SSISDB].[internal].[executions] executions 
WHERE executions.execution_id = *Your Execution Id* AND tasks.JobId = executions.job_id
```
<sup>1</sup> cette requête est pour le dépannage objectif uniquement et ouvrez change lorsque le scénario de journalisation/Diagnostics pour la montée en puissance des processus de travail est amélioré dans le futur. 
