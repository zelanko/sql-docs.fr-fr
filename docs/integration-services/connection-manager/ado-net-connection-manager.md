---
title: "Gestionnaire de connexions ADO.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "gestionnaires de connexions [Integration Services], ADO.NET"
  - "Gestionnaire de connexions ADO.NET [Integration Services]"
  - "connexions [Integration Services], ADO.NET"
ms.assetid: fc5daa2f-0159-4bda-9402-c87f1035a96f
caps.latest.revision: 59
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 59
---
# Gestionnaire de connexions ADO.NET
  Un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] permet à un package d'accéder à des sources de données à l'aide d'un fournisseur .NET. Le gestionnaire de connexions est généralement utilisé pour accéder à des sources de données comme [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ainsi qu’à des sources de données exposées via OLE DB et XML dans des tâches personnalisées écrites en code managé dans un langage comme C#.  
  
 Quand vous ajoutez un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] à un package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions résolu en une connexion [!INCLUDE[vstecado](../../includes/vstecado-md.md)] au moment de l’exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection **Connexions** sur le package.  
  
 La propriété **ConnectionManagerType** du gestionnaire de connexions est définie sur **ADO.NET**. La valeur de **ConnectionManagerType** est qualifiée de façon à inclure le nom du fournisseur .NET utilisé par le gestionnaire de connexions.  
  
## Résolution des problèmes liés au gestionnaire de connexions ADO.NET  
 Vous pouvez consigner les appels que le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] effectue vers les fournisseurs de données externes. Vous pouvez utiliser cette fonctionnalité de journalisation pour résoudre les problèmes liés aux connexions établies par le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] avec des sources de données externes. Pour consigner les appels faits par le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] aux fournisseurs de données externes, activez la journalisation des packages et sélectionnez l’événement **Diagnostic** au niveau du package. Pour plus d’informations, consultez [Outils de dépannage pour l’exécution des packages](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
 Quand elles sont lues par un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)], les données de certains types de données date de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génèrent les résultats présentés dans le tableau ci-après.  
  
|Type de données SQL Server|Résultat|  
|--------------------------|------------|  
|**time**, **datetimeoffset**|Le package échoue s'il n'utilise pas de commandes SQL paramétrables. Pour utiliser des commandes SQL paramétrables, utilisez la tâche d'exécution SQL dans votre package. Pour plus d’informations, consultez [Tâche d’exécution de requêtes SQL](../../integration-services/control-flow/execute-sql-task.md) et [Paramètres et codes de retour dans la tâche d’exécution SQL](../Topic/Parameters%20and%20Return%20Codes%20in%20the%20Execute%20SQL%20Task.md).|  
|**datetime2**|Le gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] tronque les millisecondes.|  
  
> [!NOTE]  
>  Pour plus d’informations sur les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et leur mappage aux types de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md) et [Types de données d’Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Configuration du gestionnaire de connexions ADO.NET  
 Vous pouvez configurer un gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] de plusieurs façons :  
  
 Vous pouvez définir des propriétés au moyen du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
-   Fournissez une chaîne de connexion spécifique configurée de façon à satisfaire les exigences du fournisseur .NET sélectionné.  
  
-   Selon le fournisseur, incluez le nom de la source de données à laquelle se connecter.  
  
-   Fournissez les informations d'identification de sécurité nécessaires selon le fournisseur sélectionné.  
  
-   Indiquez si la connexion créée à partir du gestionnaire de connexions est conservée au moment de l'exécution.  
  
 De nombreuses options de configuration du gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] dépendent du fournisseur .NET utilisé par le gestionnaire de connexions.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)], cliquez sur une des rubriques suivantes :  
  
-   [Configurer le gestionnaire de connexions ADO.NET](../../integration-services/connection-manager/configure-ado-net-connection-manager.md)  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md).  
  
## Voir aussi  
 [Connexions Integration Services &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  