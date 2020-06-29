---
title: Requête d’exploration de données, tâche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquerytask.f1
helpviewer_keywords:
- prediction queries [Integration Services]
- Data Mining Query task [Integration Services]
ms.assetid: f489348c-2008-4f66-8c2c-c07c3029439a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6bb3cea630401f92395e2ca4416c03bcd870c881
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85433576"
---
# <a name="data-mining-query-task"></a>Data Mining Query Task
  La tâche de requête d'exploration de données exécute des requêtes de prédiction basées sur les modèles d'exploration de données intégrés à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. La requête de prédiction crée une prédiction de nouvelles données à l'aide de modèles d'exploration de données. Par exemple, une requête de prédiction peut prédire le nombre de voiliers susceptibles d'être vendus pendant les mois d'été ou générer la liste des prospects susceptibles d'acheter un voilier.  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] met à votre disposition des tâches qui effectuent d’autres opérations Business Intelligence, telles que l’exécution d’instructions DDL (Data Definition Language) et le traitement d’objets analytiques.  
  
 Pour plus d'informations sur les autres tâches Business Intelligence, cliquez sur l'une des rubriques suivantes :  
  
-   [Tâche DDL d’exécution de SQL Server Analysis Services](analysis-services-execute-ddl-task.md)  
  
-   [Tâche de traitement d’Analysis Services](analysis-services-processing-task.md)  
  
## <a name="prediction-queries"></a>Requêtes de prédiction  
 La requête est une instruction DMX (Data Mining Extensions). Le langage DMX est une extension du langage SQL qui prend en charge l'utilisation de modèles d'exploration de données. Pour plus d’informations sur l’utilisation du langage DMX, consultez [Guide de référence du langage DMX & #40;Data Mining Extensions&#41;](/sql/dmx/data-mining-extensions-dmx-reference).  
  
 La tâche peut interroger plusieurs modèles d'exploration de données basés sur la même structure d'exploration de données. Un modèle d'exploration de données est construit à partir de l'un des algorithmes d'exploration de données fournis par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . La structure d'exploration de données référencée par la tâche de requête d'exploration de données peut comprendre plusieurs modèles d'exploration de données, construits à partir de différents algorithmes. Pour plus d’informations, consultez [Structures d’exploration de données &#40;Analysis Services - exploration de données&#41;](https://docs.microsoft.com/analysis-services/data-mining/mining-structures-analysis-services-data-mining) et [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining).  
  
 La requête de prédiction exécutée par la tâche de requête d'exploration de données renvoie un résultat qui se présente sous la forme d'une seule ligne ou d'un ensemble de données. Une requête qui ne retourne qu'une ligne est appelée « requête singleton » : par exemple, la requête qui prédit le nombre de voiliers susceptibles d'être vendus pendant les mois d'été retourne un nombre. Pour plus d’informations sur les requêtes de prédiction qui retournent une seule ligne, consultez [interfaces de requête d’exploration de données](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools).  
  
 Les résultats des requêtes sont enregistrés dans des tables. Si une table portant le nom spécifié par la tâche de requête d'exploration de données existe déjà, la tâche peut créer une nouvelle table à partir du même nom, auquel elle ajoute un nombre, ou bien remplacer le contenu de la table.  
  
 Si le résultat comprend une imbrication, elle est mise à plat avant d'être enregistrée. La mise à plat d'un résultat change en table un ensemble de résultats imbriqué. Par exemple, la mise à plat d'un résultat imbriqué composé d'une colonne **Customer** et d'une colonne **Product** imbriquée ajoute des lignes à la colonne **Customer** afin de créer une table qui comprend les données de produit associées à chaque client. Ainsi, dans le cas d'un client auquel sont associés trois produits différents, l'opération génère une table de trois lignes, contenant chacune le nom du client et un nom de produit différent. Si le mot clé FLATTENED est omis, la table ne contient que la colonne **Customer** et une seule ligne par client. Pour plus d’informations, consultez [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).  
  
## <a name="configuration-of-the-data-mining-query-task"></a>Configuration de la tâche de requête d'exploration de données  
 La tâche de requête d'exploration de données requiert deux connexions. La première connexion est celle d’un gestionnaire de connexions [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ou à un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui contient la structure et le modèle d’exploration de données. La seconde connexion est celle d'un gestionnaire de connexions OLE DB à la base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui contient la table dans laquelle la tâche écrit les données. Pour plus d'informations, consultez [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md) et [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tâche de requête d’exploration de données &#40;onglet Modèle d’exploration de données&#41;](../data-mining-query-task-editor-mining-model-tab.md)  
  
-   [Éditeur de tâche de requête d’exploration de données &#40;onglet Requête&#41;](../data-mining-query-task-editor-query-tab.md)  
  
-   [Éditeur de tâche de requête d’exploration de données &#40;onglet Sortie&#41;](../data-mining-query-task-editor-output-tab.md)  
  
> [!NOTE]  
>  L'éditeur de tâche de requête d'exploration de données n'a pas de page Expressions. À la place, utilisez la fenêtre **Propriétés** pour accéder aux outils de création et de gestion des expressions des propriétés de la tâche de requête d'exploration de données.  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-data-mining-query-task"></a>Configuration par programmation de la tâche de requête d'exploration de données  
 Pour plus d'informations sur la définition par programmation de ces propriétés, cliquez sur l'une des rubriques suivantes :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.DMQueryTask.DMQueryTask>  
  
  
