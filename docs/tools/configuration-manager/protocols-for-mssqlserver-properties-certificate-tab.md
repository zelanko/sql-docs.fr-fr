---
title: Propriétés de Protocoles pour MSSQLSERVER (onglet Certificat) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.computermgr.cert.general.f1
helpviewer_keywords:
- MSSQLSERVER property protocols
ms.assetid: 776addd6-25f3-4875-9a71-064035787090
caps.latest.revision: 17
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 3291b07cc3ba2c16fcee48d896ad850a91256a67
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "42786510"
---
# <a name="protocols-for-mssqlserver-properties-certificate-tab"></a>Propriétés de Protocoles pour MSSQLSERVER (onglet Certificat)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  L'onglet **Certificat** de la boîte de dialogue **Propriétés de Protocoles pour MSSQLSERVER** vous permet de sélectionner un certificat pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ou d'afficher les propriétés d'un certificat. Tous les champs sont vides tant qu'aucun certificat n'est sélectionné.  
  
 Les certificats sont stockés localement pour les utilisateurs de l'ordinateur. Pour charger un certificat en vue de son utilisation par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez exécuter le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sous le même compte d'utilisateur que le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="page-header"></a>En-tête de page  
 **Afficher**  
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
  
  
