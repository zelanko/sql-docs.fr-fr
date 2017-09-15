---
title: Configuration des serveurs virtuels sur IIS | Documents Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- virtual servers in RDS [ADO]
ms.assetid: 2b4786c6-40c4-4ce1-9ad4-03df436e0aff
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 10edd98f77c0aaeae05d25e76ad76a15b99bc1ed
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="configuring-virtual-servers-on-iis"></a>Configuration des serveurs virtuels sur IIS
Lorsque vous créez des serveurs virtuels dans Internet Information Services 4.0, les deux étapes supplémentaires suivantes sont nécessaires pour configurer le serveur virtuel pour travailler avec les services Bureau à distance :  
  
1.  Lorsque vous configurez le serveur, consultez « Autoriser l’accès Execute ».  
  
2.  Déplacez msadcs.dll à *vroot*\msadc, où *vroot* est le répertoire racine de votre serveur virtuel.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et Windows Server 2012, les composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (consultez Windows 8 et [Cookbook de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client Bureau à distance seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. La migration vers les applications qui utilisent des services Bureau à distance [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base de RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)



