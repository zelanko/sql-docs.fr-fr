---
title: Configuration de RDS sur Windows 2000 | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS configuration [ADO], Windows 2000
ms.assetid: ef37e858-c05f-4f52-a65f-3ce6037e0d03
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee1d76052402ab775e9e8de20e1ef6da07e23432
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63214791"
---
# <a name="configuring-rds-on-windows-2000"></a>Configuration de RDS sur Windows 2000
Si vous rencontrez des difficultés pour faire fonctionner correctement une fois que vous mettez à niveau vers Windows 2000 RDS, suivez ces étapes pour résoudre le problème :  
  
1.  Assurez-vous que le premier que le Service de publication World Wide Web est en cours d’exécution en accédant à https:// server à l’aide d’Internet Explorer. Si vous ne pouvez pas accéder au serveur de Web de cette manière, ouvrez une invite de commandes et entrez la commande suivante, « NET démarrer W3SVC ».  
  
2.  Dans le menu Démarrer, sélectionnez Exécuter. Tapez msdfmap.ini et puis cliquez sur OK pour ouvrir le fichier msdfmap.ini dans le bloc-notes. Consultez la section [CONNECT DEFAULT] et si le paramètre d’accès est la valeur NOACCESS, modifiez-le en lecture seule.  
  
3.  À l’aide de l’utilitaire RegEdit, accédez à « HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DataFactory\HandlerInfo » et assurez-vous que **HandlerRequired** est définie sur 0 et **DefaultHandler** est « » (chaîne vide).  
  
     **Remarque** si vous apportez des modifications à cette section du Registre, vous devez arrêter et redémarrer le Service de publication World Wide Web en entrant les commandes suivantes à une invite de commandes : « NET STOP W3SVC » et « NET démarrer W3SVC ».  
  
4.  À l’aide de l’utilitaire RegEdit, accédez à « HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\W3SVC\Parameters\ADCLaunch » dans le Registre et vérifiez qu’il existe une clé nommée **RDSServer.Datafactory**. Si ce n’est pas le cas, créez-le.  
  
5.  À l’aide du Gestionnaire des Services Internet, recherchez le site Web par défaut et afficher les propriétés de la racine virtuelle MSADC. Inspectez le répertoire sécurité/adresse IP et les Restrictions de nom de domaine. Si le « accès refusé » est cochée, puis sélectionnez « Granted ».  
  
 Veillez à essayer de redémarrer le serveur si les modifications n’apparaissent ne pas pour résoudre le problème dans un premier temps.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565). Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows. Migrer des applications qui utilisent des services Bureau à distance à [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base de RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


