---
title: "Bo&#238;te de dialogue Op&#233;rations actives | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.ssms.isoperations.executions.f1"
  - "sql13.ssis.ssms.isoperations.general.f1"
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# Bo&#238;te de dialogue Op&#233;rations actives
  Utilisez la boîte de dialogue **Opérations actives** pour afficher l'état des opérations [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en cours d'exécution sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , par exemple les opérations de déploiement, de validation et d'exécution de package. Ces données sont stockées dans le catalogue SSISDB.  
  
 Pour plus d’informations sur les vues [!INCLUDE[tsql](../../includes/tsql-md.md)] associées, consultez [catalog.operations &#40;base de données SSISDB&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md), [catalog.validations &#40;base de données SSISDB&#41;](../../integration-services/system-views/catalog-validations-ssisdb-database.md) et [catalog.executions &#40;base de données SSISDB&#41;](../../integration-services/system-views/catalog-executions-ssisdb-database.md)  
  
 **Que voulez-vous faire ?**  
  
-   [Ouvrir la boîte de dialogue Opérations actives](../../integration-services/performance/active-operations-dialog-box.md#open_dialog)  
  
-   [Options](#options)  
  
##  <a name="open_dialog"></a> Ouvrir la boîte de dialogue Opérations actives  
  
1.  Ouvrir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
2.  Se connecter au moteur de base de données Microsoft SQL Server  
  
3.  Dans l’Explorateur d’objets, développez le nœud **Integration Services**, cliquez avec le bouton droit sur **SSISDB**, puis cliquez sur **Opérations actives**.  
  
## Configurer les options  
  
###  <a name="options"></a> Options  
 **Type**  
 Spécifie le type d'opération. Voici les valeurs possibles pour le champ **Type** et les valeurs correspondantes dans la colonne operations_type de la vue **catalog.operations** de Transact-SQL.  
  
|||  
|-|-|  
|Initialisation d'Integration Services|1|  
|Nettoyage des opérations (travail de l'Agent SQL)|2|  
|Nettoyage des versions du projet (travail de l'Agent SQL)|3|  
|Déployer le projet|101|  
|Restaurer le projet|106|  
|Créer et démarrer l'exécution du package|200|  
|Arrêter l'opération (arrêt d'une validation ou d'une exécution)|202|  
|Valider le projet|300|  
|Valider le package|301|  
|Configurer le catalogue|1000|  
  
 **Arrêter**  
 Cliquez pour arrêter une opération en cours d'exécution.  
  
  