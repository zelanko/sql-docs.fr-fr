---
title: "Protocoles pour les propriétés MSSQLSERVER (onglet certificat) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.computermgr.cert.general.f1
helpviewer_keywords: MSSQLSERVER property protocols
ms.assetid: 776addd6-25f3-4875-9a71-064035787090
caps.latest.revision: "17"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 906539a3d5bf160a7d4eae77f5503830becb0b72
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="protocols-for-mssqlserver-properties-certificate-tab"></a>Propriétés de Protocoles pour MSSQLSERVER (onglet Certificat)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Utilisez le **certificat** onglet sur le **protocoles pour MSSQLSERVER propriétés** boîte de dialogue pour sélectionner un certificat pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou pour afficher les propriétés d’un certificat. Tous les champs sont vides tant qu'aucun certificat n'est sélectionné.  
  
 Les certificats sont stockés localement pour les utilisateurs de l'ordinateur. Pour charger un certificat en vue de son utilisation par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez exécuter le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sous le même compte d'utilisateur que le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="page-header"></a>En-tête de page  
 **Affichage**  
 Fournit des détails supplémentaires sur le certificat. Cette option n'est disponible qu'une fois qu'un certificat est sélectionné dans la zone **Certificat** . Pour plus d'informations sur les détails des certificats, consultez la documentation [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Désactiver**  
 Supprime la sélection de la zone **Certificat** .  
  
 **Certificat**  
 Nom de certificat tel que déterminé par le fournisseur de sécurité. Sélectionnez un certificat pour en afficher les détails dans la grille des propriétés.  
  
## <a name="options"></a>Options  
 Date d'expiration  
 Date de fin de la période de validité du certificat.  
  
 Nom convivial  
 Nom convivial ou courant représentant la personne ou l'Autorité de certification destinataire du certificat.  
  
 Émis par  
 Informations relatives à l'Autorité de certification qui a émis le certificat.  
  
 Délivré à  
 Informations relatives au destinataire du certificat.  
  
  
