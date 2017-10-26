---
title: Destination SQL Server Compact Edition | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.sqlservercompactdest.f1
helpviewer_keywords:
- destinations [Integration Services], SQL Server Compact
- SQL Server Compact, destination
- inserting data
ms.assetid: 697742ba-cc14-414d-8187-1845ad0dd99b
caps.latest.revision: 56
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ec7fef9755b0bfd277282de54696d6f6cff5547c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="sql-server-compact-edition-destination"></a>Destination SQL Server Compact Edition
  La destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact écrit des données dans des bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
> [!NOTE]  
>  Sur un ordinateur 64 bits, vous devez exécuter les packages qui se connectent à des sources de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact en mode 32 bits. Le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact utilisé par [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour se connecter à des sources de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact n’est disponible qu’en version 32 bits.  
  
 Vous configurez la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact en spécifiant le nom de la table dans laquelle la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact insère les données. La propriété personnalisée TableName de la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact contient le nom de la table.  
  
 Cette destination utilise un gestionnaire de connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact pour se connecter à une source de données et le gestionnaire de connexions indique le fournisseur OLE DB à utiliser. Pour plus d’informations, consultez [Gestionnaire de connexions de SQL Server Compact Edition](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md).  
  
 La destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact comporte la propriété personnalisée TableName qui peut être mise à jour par une expression de la propriété lors du chargement du package. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41;](../../integration-services/expressions/integration-services-ssis-expressions.md), [Expressions de propriété dans des packages](../../integration-services/expressions/use-property-expressions-in-packages.md) et [Propriétés personnalisées de la destination SQL Server Compact Edition](../../integration-services/data-flow/sql-server-compact-edition-destination-custom-properties.md).  
  
 La destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact comporte une entrée et ne prend pas en charge les sorties d'erreurs.  
  
## <a name="configuration-of-the-sql-server-compact-edition-destination"></a>Configuration de la destination SQL Server Compact Edition  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programme, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Propriétés personnalisées de la destination SQL Server](../../integration-services/data-flow/sql-server-destination-custom-properties.md)  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur la définition des propriétés de ce composant, consultez [Définir les propriétés d’un composant de flux de données](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de données](../../integration-services/data-flow/data-flow.md)  
  
  

