---
title: Configuration de serveurs virtuels sur IIS | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- virtual servers in RDS [ADO]
ms.assetid: 2b4786c6-40c4-4ce1-9ad4-03df436e0aff
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f11a031189cd184b2ad91430a059a0352c8fc18c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47684254"
---
# <a name="configuring-virtual-servers-on-iis"></a>Configuration de serveurs virtuels sur IIS
Lorsque vous créez des serveurs virtuels dans Internet Information Services 4.0, les deux étapes supplémentaires suivantes sont nécessaires pour configurer le serveur virtuel pour travailler avec les services Bureau à distance :  
  
1.  Lorsque vous configurez le serveur, consultez « Autoriser l’accès Execute ».  
  
2.  Déplacez msadcs.dll à *vroot*\msadc, où *vroot* est le répertoire de base de votre serveur virtuel.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base de RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


