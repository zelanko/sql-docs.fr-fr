---
title: Essentials du Package SSIS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- package requirements
ms.assetid: b0c86c35-e3d3-4724-9a96-4087e9d74bf3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3a12fb33db8b1b4da1b33c02850a108b1e30b2d2
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58390797"
---
# <a name="ssis-package-essentials"></a>Notions fondamentales sur le package SSIS
  Un package est l'objet qui implémente les fonctionnalités [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] pour extraire, transformer et charger des données. Vous créez un package en utilisant le Concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Vous pouvez aussi créer un package en exécutant l'Assistant Importation et Exportation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou l'Assistant Projet de connexions [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Pour plus d’informations, [créer des Packages dans SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) dans le concepteur SSIS et [Assistant Importation de projet](../../2014/integration-services/import-project-wizard.md).  
  
 Un package de base inclut les éléments suivants :  
  
 **Éléments de flux de contrôle**  
 Ces éléments requis effectuent différentes fonctions, fournissent une structure et contrôlent l'ordre dans lequel les éléments s'exécutent. Les éléments de flux de contrôle principaux sont les tâches, les conteneurs et les contraintes de précédence. Il doit y avoir au moins un élément de flux de contrôle dans un package.  
  
 Pour plus d’informations, consultez [Control Flow](control-flow/control-flow.md).  
  
 **Éléments de flux de données**  
 Ces éléments facultatifs extraient, modifient et chargent des données dans des sources de données. Les principaux éléments de flux de données sont les sources, les transformations et les destinations. Il n'est pas nécessaire qu'un package contienne des éléments de flux de données.  
  
 Pour en savoir plus, voir [Data Flow](data-flow/data-flow.md).  
  
 Pour obtenir un exemple montrant comment créer un package de base, consultez [leçon 1 : Création du projet et le Package de base](lesson-1-create-a-project-and-basic-package-with-ssis.md).  
  
## <a name="related-tasks"></a>Tâches associées  
  
-   [Créer des packages dans les outils de données SQL Server](create-packages-in-sql-server-data-tools.md)  
  
-   [Ajouter ou supprimer une tâche ou un conteneur dans un flux de contrôle](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
-   [Définir les propriétés d'une tâche ou d'un conteneur](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)  
  
-   [Ajouter ou supprimer un composant dans un flux de données](data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
## <a name="related-content"></a>Contenu associé  
  
1.  Vidéo, [Création d’un package de base (vidéo liée à SQL Server)](https://go.microsoft.com/fwlink/?LinkId=131023) sur MSDN.Microsoft.com  
  
## <a name="see-also"></a>Voir aussi  
 [Packages Integration Services &#40;SSIS&#41;](../../2014/integration-services/integration-services-ssis-packages.md)   
 [Contraintes de précédence](control-flow/precedence-constraints.md)  
  
  
