---
title: Boîte de dialogue opérations actives | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isoperations.executions.f1
- sql12.ssis.ssms.isoperations.general.f1
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d20e7102df982f961aed770aedc19812c5aca949
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48185879"
---
# <a name="active-operations-dialog-box"></a>Boîte de dialogue Opérations actives
  Utilisez la boîte de dialogue **Opérations actives** pour afficher l'état des opérations [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] en cours d'exécution sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , par exemple les opérations de déploiement, de validation et d'exécution de package. Ces données sont stockées dans le catalogue SSISDB.  
  
 Pour plus d’informations sur les vues [!INCLUDE[tsql](../includes/tsql-md.md)] associées, consultez [catalog.operations &#40;base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database), [catalog.validations &#40;base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-validations-ssisdb-database) et [catalog.executions &#40;base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database)  
  
 **Que voulez-vous faire ?**  
  
1.  [Ouvrez la boîte de dialogue opérations actives](#open_dialog)  
  
2.  [Configurer les options](#options)  
  
##  <a name="open_dialog"></a> Ouvrir la boîte de dialogue Opérations actives  
  
1.  Ouvrez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
2.  Se connecter au moteur de base de données Microsoft SQL Server  
  
3.  Dans l’Explorateur d’objets, développez le nœud **Integration Services** , cliquez avec le bouton droit sur **SSISDB**, puis cliquez sur **Opérations actives**.  
  
##  <a name="options"></a> Configurer les options  
  
### <a name="options"></a>Options  
 **Type**  
 Spécifie le type d'opération. Les éléments suivants sont les valeurs possibles pour le **Type** champ et les valeurs correspondantes dans la colonne operations_type de l’instruction Transact-SQL `catalog.operations` vue.  
  
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
  
  
