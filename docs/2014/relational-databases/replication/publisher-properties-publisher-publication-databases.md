---
title: Propriétés du serveur de publication - Serveur de publication, Bases de données de publication | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.pubproperties.pubdb.f1
helpviewer_keywords:
- Publisher Properties dialog box
ms.assetid: 574ea2e7-4e7b-4733-ab52-429ca93c7b0a
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a05c853ff23e0b10434a5e4abc072c950b1cb713
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37276655"
---
# <a name="publisher-properties---publisher-publication-databases"></a>Propriétés du serveur de publication - Serveur de publication, Bases de données de publication
  La page **Bases de données de publication** de la boîte de dialogue **Propriétés du serveur de publication** permet à un utilisateur dans le rôle serveur fixe **sysadmin** d'autoriser la réplication des bases de données. L'activation d'une base de données ne publie pas la base de données ; elle permet à un utilisateur du rôle fixe de base de données **db_owner** de créer des publications dans la base de données.  
  
## <a name="options"></a>Options  
 **Transactionnelle**  
 Activez cette case à cocher pour permettre aux utilisateurs du rôle de base de données fixe **db_owner** de créer des publications d'instantanés ou des publications transactionnelles dans la base de données.  
  
 **Fusion**  
 Activez cette case à cocher pour permettre aux utilisateurs du rôle de base de données fixe **db_owner** de créer des publications de fusion dans la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les propriétés d’un serveur de distribution et d’un serveur de publication](view-and-modify-distributor-and-publisher-properties.md)   
 [Référence des propriétés &#40;réplication&#41;](properties-reference-replication.md)  
  
  
