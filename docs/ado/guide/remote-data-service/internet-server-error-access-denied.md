---
title: 'Erreur du serveur Internet : Accès refusé | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- access denied error in RDS [ADO]
ms.assetid: e5b43cfa-da8d-430d-a2ab-5443dda47a16
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 1a7dbb125c3a320ac380d91b71aff7826c17e15d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718318"
---
# <a name="internet-server-error-access-denied"></a>Erreur du serveur Internet : accès refusé
Si vous obtenez cette erreur, cela signifie généralement que Microsoft Internet Information Services (IIS) a retourné l’état suivant :  
  
 HTTP_STATUS_DENIED 401  
  
 Assurez-vous que les répertoires accédés par IIS disposent des autorisations nécessaires. Services Bureau à distance peut communiquer avec un serveur Web IIS en cours d’exécution dans l’un des trois modes d’authentification de mot de passe : Anonyme, Basic ou stimulation/réponse NT (appelée authentification Windows intégrée dans Windows 2000). En outre, le serveur Web doit avoir des autorisations sur l’ordinateur de source de données s’il s’agit d’un ordinateur Windows NT/Windows 2000.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base de RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)




