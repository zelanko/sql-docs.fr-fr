---
title: Gestionnaire de connexions ADO.NET | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connection managers [Integration Services], ADO.NET
- ADO.NET connection manager [Integration Services]
- connections [Integration Services], ADO.NET
ms.assetid: fc5daa2f-0159-4bda-9402-c87f1035a96f
caps.latest.revision: 59
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 44b07e26877a4d53d87cabb2ce48894f067a2802
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36155319"
---
# <a name="adonet-connection-manager"></a>Gestionnaire de connexions ADO.NET
  Un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] permet à un package d'accéder à des sources de données à l'aide d'un fournisseur .NET. Le gestionnaire de connexions est généralement utilisé pour accéder à des sources de données comme [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ainsi qu’à des sources de données exposées via OLE DB et XML dans des tâches personnalisées écrites en code managé dans un langage comme C#.  
  
 Lorsque vous ajoutez un [!INCLUDE[vstecado](../../includes/vstecado-md.md)] Gestionnaire de connexions à un package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée une connexion de gestionnaire qui est résolu comme un [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connexion en cours d’exécution, définit les propriétés du Gestionnaire des connexions et ajoute le Gestionnaire de connexions le `Connections` collection sur le package.  
  
 Le `ConnectionManagerType` du Gestionnaire de connexions est définie sur `ADO.NET`. La valeur de `ConnectionManagerType` est qualifiée de façon à inclure le nom du fournisseur .NET utilisé par le Gestionnaire de connexion.  
  
## <a name="adonet-connection-manager-troubleshooting"></a>Résolution des problèmes liés au gestionnaire de connexions ADO.NET  
 Vous pouvez consigner les appels que le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] effectue vers les fournisseurs de données externes. Vous pouvez utiliser cette fonctionnalité de journalisation pour résoudre les problèmes liés aux connexions établies par le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] avec des sources de données externes. Pour consigner les appels faits par le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] aux fournisseurs de données externes, activez la journalisation des packages et sélectionnez l’événement **Diagnostic** au niveau du package. Pour plus d’informations, consultez [Outils de dépannage pour l’exécution des packages](../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
 Quand elles sont lues par un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] , les données de certains types de données date de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génèrent les résultats présentés dans le tableau ci-après.  
  
|Type de données SQL Server|Résultats|  
|--------------------------|------------|  
|`time`, `datetimeoffset`|Le package échoue s'il n'utilise pas de commandes SQL paramétrables. Pour utiliser des commandes SQL paramétrables, utilisez la tâche d'exécution SQL dans votre package. Pour plus d’informations, consultez [Tâche d’exécution de requêtes SQL](../control-flow/execute-sql-task.md) et [Paramètres et codes de retour dans la tâche d’exécution SQL](../parameters-and-return-codes-in-the-execute-sql-task.md).|  
|`datetime2`|Le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] tronque les millisecondes.|  
  
> [!NOTE]  
>  Pour plus d’informations sur les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et leur mappage aux types de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) et [Types de données d’Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="adonet-connection-manager-configuration"></a>Configuration du gestionnaire de connexions ADO.NET  
 Vous pouvez configurer un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] de plusieurs façons :  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
-   Fournissez une chaîne de connexion spécifique configurée de façon à satisfaire les exigences du fournisseur .NET sélectionné.  
  
-   Selon le fournisseur, incluez le nom de la source de données à laquelle se connecter.  
  
-   Fournissez les informations d'identification de sécurité nécessaires selon le fournisseur sélectionné.  
  
-   Indiquez si la connexion créée à partir du gestionnaire de connexions est conservée au moment de l'exécution.  
  
 De nombreuses options de configuration du gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] dépendent du fournisseur .NET utilisé par le gestionnaire de connexions.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans le Concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , cliquez sur une des rubriques suivantes :  
  
-   [Configurer le Gestionnaire de connexions ADO.NET](../configure-ado-net-connection-manager.md)  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programme, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Services d’intégration &#40;SSIS&#41; connexions](integration-services-ssis-connections.md)  
  
  
