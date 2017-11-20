---
title: Les certificats dans Sql Server Integration Services monter en charge | Documents Microsoft
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2970b2b2cc7cf30c18a203ebbb92b5418bfc9be5
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="deal-with-certificates-in-sql-server-integration-services-scale-out"></a>Les certificats dans SQL Server Integration Services monter en charge

Pour sécuriser la communication entre l’échelle des principales et de montée en puissance des processus de travail, deux certificats sont utilisés dans monter en charge, par exemple, certificat de mise à l’échelle des Master et montée en puissance des processus de travail. 

## <a name="scale-out-master-certificate"></a>Certificat de mise à l’échelle des principale

Dans la plupart des cas, certificat de mise à l’échelle des principale est configuré pendant l’installation de la mise à l’échelle des Master.

Dans le **Configuration Integration Services échelle Out - nœud maître** page de l’Assistant d’Installation de SQL Server, vous pouvez soit créer un nouveau certificat SSL auto-signé ou utiliser un certificat SSL existant.

![Configuration de master](media/master-config.PNG)

Si vous n’avez des spécifications spéciales sur les certificats, vous pouvez choisir de créer un nouveau certificat SSL auto-signé. Vous pouvez également spécifier les noms communs du certificat. Assurez-vous que le nom d’hôte du point de terminaison maître utilisée ultérieurement par montée en puissance des processus de travail est inclus dans les noms communs. Par défaut, le nom de l’ordinateur et l’adresse ip du nœud principal sont inclus. 

Si vous choisissez d’utiliser un certificat existant, cliquez sur « Parcourir … » pour sélectionner un certificat SSL à partir de **racine** magasin de certificats de l’ordinateur local.

### <a name="change-scale-out-master-certificate"></a>Modifier le certificat de l’échelle des principales

Voulez-vous modifier votre certificat de mise à l’échelle des Master en raison de l’expiration du certificat ou d’autres raisons. Suivez les étapes ci-dessous :

#### <a name="1-create-a-ssl-certificate"></a>1. Créer un certificat SSL.
Créer et installer un certificat SSL sur Master nœud avec la commande suivante :
```dos
MakeCert.exe -n CN={master endpoint host} SSISScaleOutMaster.cer -r -ss Root -sr LocalMachine
```
Exemple :
```dos
MakeCert.exe -n CN=MasterMachine SSISScaleOutMaster.cer -r -ss Root -sr LocalMachine
```

#### <a name="2-bind-the-certificate-to-master-port"></a>2. Lier le certificat Master port
Vérifiez la liaison d’origine avec la commande suivante :
```dos
netsh http show sslcert ipport=0.0.0.0:{Master port}
```
Exemple :
```dos
netsh http show sslcert ipport=0.0.0.0:8391
```
Supprimer la liaison d’origine et configurer la nouvelle liaison avec les commandes suivantes :
```dos
netsh http delete sslcert ipport=0.0.0.0:{Master port}
netsh http add sslcert ipport=0.0.0.0:{Master port} certhash={SSL Certificate Thumbprint} certstorename=Root appid={original appid}
```
Exemple :
```dos
netsh http delete sslcert ipport=0.0.0.0:8391
netsh http add sslcert ipport=0.0.0.0:8391 certhash=01d207b300ca662f479beb884efe6ce328f77d53 certstorename=Root appid={a1f96506-93e0-4c91-9171-05a2f6739e13}
```
#### <a name="3-update-scale-out-master-service-configuration-file"></a>3. Mettre à jour le fichier de configuration de service de mise à l’échelle des principale
Fichier de configuration de service de mise à l’échelle des principale de mise à jour, \<pilote\>: \Program Files\Microsoft Server\140\DTS\Binn\MasterSettings.config SQL, sur contrôleur de nœud. Mise à jour **SSLCertThumbprint** l’empreinte numérique du nouveau certificat SSL.

#### <a name="4-restart-scale-out-master-service"></a>4. Redémarrez le service de mise à l’échelle des principales

#### <a name="5-reconnect-scale-out-worker-to-scale-out-master"></a>5. Reconnectez la montée en charge de travail pour la montée en puissance parallèle principale
Pour chaque mise à l’échelle des processus de travail, soit supprimer le processus de travail et ajoutez-le de nouveau avec [échelle Out Manager](integration-services-ssis-scale-out-manager.md) ou suivez les étapes 5.1 à 5.3 :

5.1 installer le certificat SSL client dans le magasin racine de l’ordinateur local sur le nœud de travail

5.2 mise à jour de l’échelle Out Worker service fichier montée en puissance de mise à jour des Worker service configuration fichier de configuration, \<pilote\>: \Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config, sur le nœud de travail. Mise à jour **MasterHttpsCertThumbprint** l’empreinte numérique du nouveau certificat SSL.

5.3 redémarrer la mise à l’échelle service de travail


## <a name="scale-out-worker-certificate"></a>Certificat de la montée en puissance des processus de travail

Certificat de la montée en puissance des processus de travail est généré automatiquement lors de l’installation de mise à l’échelle des processus de travail. 

### <a name="change-scale-out-worker-certificate"></a>Modifier le certificat de montée en puissance des processus de travail

Dans les cas à modifier le certificat de la montée en puissance des processus de travail, suivez les étapes ci-dessous.

#### <a name="1-create-a-certificate"></a>1. Créer un certificat
Créer et installer un certificat avec la commande suivante :
```dos
MakeCert.exe -n CN={worker machine name};CN={worker machine ip} SSISScaleOutWorker.cer -r -ss My -sr LocalMachine
```
Exemple :
```dos
MakeCert.exe -n CN=WorkerMachine;CN=10.0.2.8 SSISScaleOutWorker.cer -r -ss My -sr LocalMachine
```
#### <a name="2-install-the-client-certificate-to-the-root-store-of-local-machine-on-worker-node"></a>2. Installez le certificat de client dans le magasin racine de l’ordinateur local sur le nœud de travail

#### <a name="3-give-service-access-to-the-certificate"></a>3. Donner accès au service pour le certificat
Supprimez l’ancien certificat et donner accès au service de mise à l’échelle des processus de travail vers le nouveau certificat avec la commande :
```dos
certmgr.exe /del /c /s /r localmachine My /n {CN of the old certificate}
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s {CN of the new certificate} -a {the account running Scale Out Worker service}
```
Exemple :
```dos
certmgr.exe /del /c /s /r localmachine My /n WorkerMachine
winhttpcertcfg.exe -g -c LOCAL_MACHINE\My -s WorkerMachine -a SSISScaleOutWorker140
```
#### <a name="4-update-scale-out-worker-configuration-file"></a>4. Mettre à jour le fichier de configuration de montée en puissance des processus de travail
Fichier de configuration de service de mise à l’échelle des processus de travail de mise à jour, \<pilote\>: \Program Files\Microsoft SQL Server\140\DTS\Binn\WorkerSettings.config, sur le nœud de travail. Mise à jour **WorkerHttpsCertThumbprint** l’empreinte numérique du nouveau certificat.

#### <a name="5-install-the-client-certificate-to-the-root-store-of-local-machine-on-master-node"></a>5. Installez le certificat de client dans le magasin racine de l’ordinateur local sur Master nœud

#### <a name="6-restart-scale-out-worker-service"></a>6. Redémarrez le service de mise à l’échelle des processus de travail

