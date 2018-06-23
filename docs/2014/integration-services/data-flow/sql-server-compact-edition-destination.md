---
title: Destination SQL Server Compact Edition | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.sqlservercompactdest.f1
helpviewer_keywords:
- destinations [Integration Services], SQL Server Compact
- SQL Server Compact, destination
- inserting data
ms.assetid: 697742ba-cc14-414d-8187-1845ad0dd99b
caps.latest.revision: 56
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 59754dabe5cfb4da9fc131874fb6e04057cee959
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040202"
---
# <a name="sql-server-compact-edition-destination"></a>Destination SQL Server Compact Edition
  La destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact écrit des données dans des bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
> [!NOTE]  
>  Sur un ordinateur 64 bits, vous devez exécuter les packages qui se connectent à des sources de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact en mode 32 bits. Le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact utilisé par [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour se connecter à des sources de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact n’est disponible qu’en version 32 bits.  
  
 Vous configurez la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact en spécifiant le nom de la table dans laquelle la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact insère les données. La propriété personnalisée TableName de la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact contient le nom de la table.  
  
 Cette destination utilise un gestionnaire de connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact pour se connecter à une source de données et le gestionnaire de connexions indique le fournisseur OLE DB à utiliser. Pour plus d’informations, consultez [Gestionnaire de connexions de SQL Server Compact Edition](../connection-manager/sql-server-compact-edition-connection-manager.md).  
  
 La destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact comporte la propriété personnalisée TableName qui peut être mise à jour par une expression de la propriété lors du chargement du package. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41;](../expressions/integration-services-ssis-expressions.md), [Expressions de propriété dans des packages](../expressions/use-property-expressions-in-packages.md) et [Propriétés personnalisées de la destination SQL Server Compact Edition](sql-server-compact-edition-destination-custom-properties.md).  
  
 La destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact comporte une entrée et ne prend pas en charge les sorties d'erreurs.  
  
## <a name="configuration-of-the-sql-server-compact-edition-destination"></a>Configuration de la destination SQL Server Compact Edition  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../common-properties.md)  
  
-   [Propriétés personnalisées de la destination SQL Server](sql-server-destination-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Pour plus d’informations sur la définition des propriétés de ce composant, consultez [Définir les propriétés d’un composant de flux de données](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de données](data-flow.md)  
  
  