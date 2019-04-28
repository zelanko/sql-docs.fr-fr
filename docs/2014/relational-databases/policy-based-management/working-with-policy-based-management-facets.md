---
title: Utiliser les facettes de la gestion basée sur des stratégies | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- viewing Policy-Based Management facets
- facets [Policy-Based Management], copying
- facets [Policy-Based Management], viewing
- copying Policy-Based Management facets
ms.assetid: 88d025c4-07c2-4e4d-8634-204249a8c82c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 037eb57f53bf583195efdf1f91fcd55f94ebaddc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62676904"
---
# <a name="working-with-policy-based-management-facets"></a>Utiliser les facettes de la gestion basée sur des stratégies
  Une facette de la gestion basée sur des stratégies est un ensemble de propriétés logiques liées à une zone d'intérêt de gestion. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inclut plusieurs facettes prédéfinies. Par exemple, la facette Configuration de la surface d'exposition définit en tant que propriétés les fonctionnalités qui sont désactivées par défaut.  
  
 Lorsque vous gérez de nombreux environnements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] similaires, vous pouvez configurer une facette dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], copier l’état de cette facette dans un fichier, puis importer ce fichier dans une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en tant que stratégie. Une fois l'état converti en stratégie, cette stratégie peut être appliquée à d'autres instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], à des objets d'instance, à des bases de données ou à des objets de base de données.  
  
 Cette rubrique décrit comment copier l'état d'une facette dans un fichier XML.  
  
##  <a name="BeforeYouBegin"></a> Autorisations  
 Les procédures de cette rubrique nécessite l’appartenance au rôle PolicyAdministratorRole dans la base de données msdb.  
  
## <a name="viewing-and-copying-facet-states"></a>Affichage et copie d'états de facette  
 [Afficher les facettes de gestion basée sur des stratégies sur un objet SQL Server](view-the-policy-based-management-facets-on-a-sql-server-object.md)  
  
 [Copier un état de facette de gestion basée sur des stratégies dans un fichier XML](copy-a-policy-based-management-facet-state-to-an-xml-file.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](administer-servers-by-using-policy-based-management.md)  
  
  
