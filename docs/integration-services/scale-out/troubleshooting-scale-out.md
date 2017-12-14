---
title: "Résolution des problèmes liés à SQL Server Integration Services (SSIS) Scale Out | Microsoft Docs"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 56d61bc6ba76514ba2291243002a7423ec8e265c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="troubleshooting-scale-out"></a>Résolution des problèmes liés à Scale Out

SSIS Scale Out implique la communication entre SSISDB, le service Scale Out Master et le service Scale Out Worker. Parfois, la communication est interrompue, par exemple, en raison d’erreurs de configuration ou d’un défaut d’autorisations d’accès. Ce document vous aide à résoudre les problèmes liés à la configuration de Scale Out.

Pour étudier les problèmes que vous rencontrez, suivez les étapes ci-après une par une jusqu’à ce que votre problème soit résolu.

### <a name="symptoms"></a>**Symptômes** 
Scale Out Master ne peut pas se connecter à SSISDB. 

Les propriétés Master n’apparaissent pas dans Scale Out Manager.

Les propriétés Master ne sont pas renseignées dans [SSISDB].[catalog].[master_properties].

### <a name="solution"></a>**Solution**
Étape 1 : Vérifiez si Scale Out est activé.

Cliquez avec le bouton droit sur le nœud **SSISDB** dans l’Explorateur d’objets de SSMS, puis vérifiez que **la fonctionnalité Scale Out est activée**.

![Vérifier si Scale Out est activé](media\isenabled.PNG)

Si la valeur de propriété est False, activez Scale Out en appelant la procédure stockée [SSISDB].[catalog].[enable_scaleout].

Étape 2 : Vérifiez si le nom SQL Server spécifié dans le fichier de configuration de Scale Out Master est correct et redémarrez le service Scale Out Master.

### <a name="symptoms"></a>**Symptômes** 
Scale Out Worker ne peut pas se connecter à Scale Out Master.

Scale Out Worker n’apparaît pas une fois ajouté à Scale Out Manager.

Scale Out Worker n’apparaît pas dans [SSISDB].[catalog].[worker_agents].

Le service Scale Out Worker est en cours d’exécution, alors que Scale Out Worker est hors connexion.

### <a name="solutions"></a>**Solutions** 
Vérifiez les messages d’erreur dans le journal du service Scale Out Worker sous \<lecteur\>:\Users\\*[compte exécutant le service Worker]*\AppData\Local\SSIS\Cluster\Agent.

**Cas** 

System.ServiceModel.EndpointNotFoundException : Il n’existait pas de point de terminaison à l’écoute sur https://*[nom_machine]:[port]*/ClusterManagement/ pouvant accepter le message.

Étape 1 : Vérifiez si le numéro de port spécifié dans le fichier de configuration du service Scale Out Master est correct et redémarrez le service Scale Out Master. 

Étape 2 : Vérifiez si le point de terminaison maître spécifié dans la configuration du service Scale Out Worker est correct et redémarrez le service Scale Out Worker.

Étape 3 : Vérifiez si le port de pare-feu est ouvert sur le nœud Scale Out Master.

Étape 4 : Résolvez tout problème de connexion entre les nœuds Scale Out Master et Scale Out Worker.

**Cas**

System.ServiceModel.Security.SecurityNegotiationException : Impossible d’établir une relation d’approbation pour le canal sécurisé SSL/TLS avec l’autorité '*[nom_machine]:[port]*'. ---> System.Net.WebException : La connexion sous-jacente a été fermée : Impossible d’établir une relation de confiance pour le canal sécurisé SSL/TLS. ---> System.Security.Authentication.AuthenticationException : Le certificat distant n’est pas valide selon la procédure de validation.

Étape 1 : Installez le certificat Scale Out Master dans le magasin de certificats racine de l’ordinateur local sur le nœud Scale Out Worker si ce n’est déjà fait, puis redémarrez le service Scale Out Worker.

Étape 2 : Vérifiez si le nom d’hôte dans le point de terminaison maître est inclus dans les noms communs du certificat Scale Out Master. Si ce n’est pas le cas, réinitialisez le point de terminaison maître dans le fichier de configuration de Scale Out Worker et redémarrez le service Scale Out Worker. 

> [!Note]
> Si vous ne pouvez pas changer le nom d’hôte du point de terminaison maître en raison des paramètres DNS, vous devez changer le certificat Scale Out Master. Consultez [Gérer les certificats dans SSIS Scale Out](deal-with-certificates-in-ssis-scale-out.md).

Étape 3 : Vérifiez si l’empreinte numérique du master spécifiée dans la configuration de Scale Out Worker correspond à l’empreinte du certificat Scale Out Master. 

**Cas**

System.ServiceModel.Security.SecurityNegotiationException : Impossible d’établir un canal sécurisé pour SSL/TLS avec l’autorité '*[nom_machine]:[port]*'. ---> System.Net.WebException: La demande a été abandonnée : Impossible de créer un canal sécurisé SSL/TLS.

Étape 1 : Vérifiez si le compte exécutant le service Scale Out Worker a accès au certificat Scale Out Worker à l’aide de la commande ci-après.

```dos
winhttpcertcfg.exe -l -c LOCAL_MACHINE\MY -s {CN of the worker certificate}
```

Si ce n’est pas le cas, accordez l’accès à l’aide de la commande ci-après et redémarrez le service Scale Out Worker.

```dos
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s {CN of the worker certificate} -a {the account running Scale Out Worker service}
```

**Cas**

System.ServiceModel.Security.MessageSecurityException: La requête HTTP a été interdite avec le schéma d’authentification client 'Anonyme'. ---> System.Net.WebException: Le serveur distant a retourné une erreur : (403) Interdit.

Étape 1 : Installez le certificat Scale Out Worker dans le magasin de certificats racine de l’ordinateur local sur le nœud Scale Out Master si ce n’est déjà fait, puis redémarrez le service Scale Out Worker.

Étape 2 : Nettoyez les certificats inutiles dans le magasin de certificats racine de l’ordinateur local sur le nœud Scale Out Master.

Étape 3 : Configurez Schannel pour ne plus envoyer la liste des autorités de certification racine de confiance pendant le processus de négociation TLS/SSL, en ajoutant l’entrée de Registre ci-après au nœud Scale Out Master.

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL

Nom de la valeur : SendTrustedIssuerList 

Type de valeur : REG_DWORD 

Données de valeur : 0 (False)

**Cas**

System.ServiceModel.CommunicationException : Une erreur s’est produite lors de la requête HTTP à https://*[nom_machine]:[port]*/ClusterManagement/. Cela peut être dû au fait que le certificat de serveur n’est pas configuré correctement avec HTTP.SYS pour HTTPS. Une autre raison possible est une non-correspondance de la liaison de sécurité entre le client et le serveur. 

Étape 1 : Vérifiez si le certificat Scale Out Master est correctement lié au port dans le point de terminaison maître sur le nœud master à l’aide de la commande ci-après. Vérifiez si le hachage de certificat affiché est mis en correspondance avec l’empreinte du certificat Scale Out Master.

```dos
netsh http show sslcert ipport=0.0.0.0:{Master port}
```

Si la liaison n’est pas correcte, réinitialisez-la à l’aide des commandes suivantes et redémarrez le service Scale Out Worker.

```dos
netsh http delete sslcert ipport=0.0.0.0:{Master port}
netsh http add sslcert ipport=0.0.0.0:{Master port} certhash={Master certificate thumbprint} certstorename=Root appid={random guid}
```

### <a name="symptoms"></a>**Symptômes**
La validation échoue au moment de la connexion de Scale Out Worker à Scale Out Master dans Scale Out Manager avec le message d’erreur « Impossible d’ouvrir le magasin de certificats sur l’ordinateur ».

### <a name="solution"></a>**Solution**

Étape 1 : Exécutez Scale Out Manager en tant qu’administrateur. Si vous l’ouvrez avec SSMS, vous devez exécuter SSMS en tant qu’administrateur.

Étape 2 : Démarrez le service Registre à distance sur la machine s’il n’est pas en cours d’exécution.

### <a name="symptoms"></a>**Symptômes**
L’exécution dans Scale Out ne démarre pas.

### <a name="solution"></a>**Solution**

Vérifiez l’état des machines que vous avez sélectionnées pour exécuter le package dans [SSISDB].[catalog].[worker_agents]. Au moins un Worker doit être en ligne et activé.

### <a name="symptoms"></a>**Symptômes** 
Les packages s’exécutent correctement, mais aucun message n’est journalisé.

### <a name="solution"></a>**Solution**

Vérifiez si l’authentification SQL Server est autorisée par le serveur SQL Server qui héberge SSISDB.

> [!Note]  
> Si vous avez changé le compte pour la journalisation Scale Out, consultez [Changer le compte pour la journalisation Scale Out](change-logdb-account.md) et vérifiez la chaîne de connexion utilisée pour la journalisation.

### <a name="symptoms"></a>**Symptômes**
Les messages d’erreur dans le rapport d’exécution des packages ne sont pas suffisants pour résoudre les problèmes.

### <a name="solution"></a>**Solution**
Des journaux d’exécution supplémentaires sont disponibles sous TasksRootFolder dans WorkerSettings.config. Leur emplacement par défaut est \<lecteur\>:\Users\\*[compte]*\AppData\Local\SSIS\ScaleOut\Tasks. *[compte]* est le compte exécutant le service Scale Out Worker avec la valeur par défaut SSISScaleOutWorker140.

Pour localiser le journal de l’exécution des packages avec *[execution_id]*, exécutez la commande T-SQL ci-après pour obtenir le *[TaskId]*. Ensuite, recherchez le sous-dossier nommé avec *[TaskId]* sous TasksRootFolder.<sup> 1<sup>

```sql
SELECT [TaskId]
FROM [SSISDB].[internal].[tasks] tasks, [SSISDB].[internal].[executions] executions 
WHERE executions.execution_id = *Your Execution Id* AND tasks.JobId = executions.job_id
```
<sup>1</sup> Cette requête n’est fournie qu’à des fins de résolution de problème et pourra faire l’objet de modifications quand des améliorations seront apportées au scénario de journalisation/diagnostic pour Scale Out Worker. 
