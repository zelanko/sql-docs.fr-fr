---
title: "Gérer les certificats dans SQL Server Integration Services Scale Out | Microsoft Docs"
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
ms.openlocfilehash: e09fec1fcf9cf0221dad50d708adef773b297237
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="deal-with-certificates-in-sql-server-integration-services-scale-out"></a>Gérer les certificats dans SQL Server Integration Services Scale Out

Pour sécuriser la communication entre Scale Out Master et Scale Out Worker, deux certificats sont utilisés dans Scale Out : le certificat Scale Out Master et le certificat Scale Out Worker. 

## <a name="scale-out-master-certificate"></a>Certificat Scale Out Master

Dans la plupart des cas, le certificat Scale Out Master est configuré pendant l’installation de Scale Out Master.

Dans la page **Configuration d’Integration Services Scale Out - Nœud master** de l’Assistant Installation de SQL Server, vous pouvez créer un certificat SSL auto-signé ou utiliser un certificat SSL existant.

![Configuration de Master](media/master-config.PNG)

Si vous n’avez pas d’exigences particulières pour les certificats, vous pouvez choisir de créer un certificat SSL auto-signé. Vous pouvez ensuite spécifier les noms communs dans le certificat. Assurez-vous que le nom d’hôte du point de terminaison maître utilisé par Scale Out Worker est inclus dans les noms communs. Par défaut, le nom de machine et l’adresse IP du nœud master sont inclus. 

Si vous choisissez d’utiliser un certificat existant, cliquez sur « Parcourir… » pour sélectionner un certificat SSL à partir du magasin de certificats **racine** de l’ordinateur local.

### <a name="change-scale-out-master-certificate"></a>Changer le certificat Scale Out Master

Vous pouvez changer votre certificat Scale Out Master s’il expire ou pour d’autres raisons. Suivez les étapes ci-dessous :

#### <a name="1-create-a-ssl-certificate"></a>1. Créer un certificat SSL.
Créez et installez un certificat SSL sur le nœud master à l’aide de la commande suivante :
```dos
MakeCert.exe -n CN={master endpoint host} SSISScaleOutMaster.cer -r -ss Root -sr LocalMachine
```
Exemple :
```dos
MakeCert.exe -n CN=MasterMachine SSISScaleOutMaster.cer -r -ss Root -sr LocalMachine
```

#### <a name="2-bind-the-certificate-to-master-port"></a>2. Lier le certificat au port Master
Vérifiez la liaison d’origine à l’aide de la commande suivante :
```dos
netsh http show sslcert ipport=0.0.0.0:{Master port}
```
Exemple :
```dos
netsh http show sslcert ipport=0.0.0.0:8391
```
Supprimez la liaison d’origine et configurez la nouvelle liaison à l’aide des commandes suivantes :
```dos
netsh http delete sslcert ipport=0.0.0.0:{Master port}
netsh http add sslcert ipport=0.0.0.0:{Master port} certhash={SSL Certificate Thumbprint} certstorename=Root appid={original appid}
```
Exemple :
```dos
netsh http delete sslcert ipport=0.0.0.0:8391
netsh http add sslcert ipport=0.0.0.0:8391 certhash=01d207b300ca662f479beb884efe6ce328f77d53 certstorename=Root appid={a1f96506-93e0-4c91-9171-05a2f6739e13}
```
#### <a name="3-update-scale-out-master-service-configuration-file"></a>3. Mettre à jour le fichier de configuration du service Scale Out Master
Mettez à jour le fichier de configuration du service Scale Out Master, \<lecteur\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config, sur le nœud master. Mettez à jour **SSLCertThumbprint** vers l’empreinte du nouveau certificat SSL.

#### <a name="4-restart-scale-out-master-service"></a>4. Redémarrer le service Scale Out Master

#### <a name="5-reconnect-scale-out-worker-to-scale-out-master"></a>5. Reconnecter Scale Out Worker à Scale Out Master
Pour chaque Scale Out Worker, soit supprimez le Worker et rajoutez-le avec [Scale Out Manager](integration-services-ssis-scale-out-manager.md), soit suivez les étapes 5.1 à 5.3 ci-après :

5.1 Installez le certificat SSL client dans le magasin racine de l’ordinateur local sur le nœud Worker.

5.2 Mettez à jour le fichier de configuration du service Scale Out Worker, \<lecteur\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config, sur le nœud Worker. Mettez à jour **MasterHttpsCertThumbprint** vers l’empreinte du nouveau certificat SSL.

5.3 Redémarrez le service Scale Out Worker.


## <a name="scale-out-worker-certificate"></a>Certificat Scale Out Worker

Le certificat Scale Out Worker est généré automatiquement durant l’installation de Scale Out Worker. 

### <a name="change-scale-out-worker-certificate"></a>Changer le certificat Scale Out Worker

Si vous souhaitez changer le certificat Scale Out Worker, suivez les étapes ci-après.

#### <a name="1-create-a-certificate"></a>1. Créer un certificat
Créez et installez un certificat à l’aide de la commande suivante :
```dos
MakeCert.exe -n CN={worker machine name};CN={worker machine ip} SSISScaleOutWorker.cer -r -ss My -sr LocalMachine
```
Exemple :
```dos
MakeCert.exe -n CN=WorkerMachine;CN=10.0.2.8 SSISScaleOutWorker.cer -r -ss My -sr LocalMachine
```
#### <a name="2-install-the-client-certificate-to-the-root-store-of-local-machine-on-worker-node"></a>2. Installer le certificat client dans le magasin racine de l’ordinateur local sur le nœud Worker

#### <a name="3-give-service-access-to-the-certificate"></a>3. Donner au service l’accès au certificat
Supprimez l’ancien certificat et donnez au service Scale Out Worker l’accès au nouveau certificat à l’aide de la commande suivante :
```dos
certmgr.exe /del /c /s /r localmachine My /n {CN of the old certificate}
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s {CN of the new certificate} -a {the account running Scale Out Worker service}
```
Exemple :
```dos
certmgr.exe /del /c /s /r localmachine My /n WorkerMachine
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s WorkerMachine -a SSISScaleOutWorker140
```
#### <a name="4-update-scale-out-worker-configuration-file"></a>4. Mettre à jour le fichier de configuration de Scale Out Worker
Mettez à jour le fichier de configuration du service Scale Out Worker, \<lecteur\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config, sur le nœud Worker. Mettez à jour **WorkerHttpsCertThumbprint** vers l’empreinte du nouveau certificat.

#### <a name="5-install-the-client-certificate-to-the-root-store-of-local-machine-on-master-node"></a>5. Installer le certificat client dans le magasin racine de l’ordinateur local sur le nœud Master

#### <a name="6-restart-scale-out-worker-service"></a>6. Redémarrer le service Scale Out Worker
