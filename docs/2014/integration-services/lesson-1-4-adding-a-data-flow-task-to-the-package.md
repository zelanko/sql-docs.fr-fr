---
title: 'Étape 4 : Ajout d’une tâche de flux de données au package | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 96af3073-8f11-4444-b934-fe8613a2d084
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e36f658dc2742efba59d5a708fd5f626ea8a1609
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219449"
---
# <a name="step-4-adding-a-data-flow-task-to-the-package"></a>Étape 4 : ajout d'une tâche de flux de données au package
  Après avoir créé des gestionnaires de connexions pour les données sources et de destination, la tâche suivante consiste à ajouter une tâche de flux de données à votre package. La tâche de flux de données permet d'encapsuler le moteur de flux de données qui déplace les données entre les sources et les destinations et fournit la fonctionnalité grâce à laquelle il est possible de transformer, nettoyer et modifier les données lors de leur déplacement. La tâche de flux de données est l'endroit où s'effectue la majorité du travail d'un processus d'extraction, de transformation et de chargement (ETL).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sépare le flux de données du flux de contrôle.  
  
### <a name="to-add-a-data-flow-task"></a>Pour ajouter une tâche de flux de données  
  
1.  Cliquez sur l'onglet **Flux de contrôle** .  
  
2.  Dans la **Boîte à outils SSIS**, développez **Favoris**, puis faites glisser une **tâche de flux de données** sur l’aire de conception de l’onglet **Flux de contrôle** .  
  
    > [!NOTE]  
    >  Si la boîte à outils SSIS n'est pas disponible, dans le menu principal, sélectionnez SSIS, puis Boîte à outils SSIS pour afficher cette dernière.  
  
3.  Sur le **flux de contrôle** aire de conception, cliquez sur récemment ajouté **Data Flow Task**, cliquez sur **renommer**et remplacez le nom par `Extract Sample Currency Data`.  
  
     Il est préférable d'affecter des noms uniques aux composants que vous ajoutez à une zone de conception. Afin d'utiliser et de maintenir les composants plus facilement, il est conseillé de leur affecter des noms décrivant les fonctions qu'ils effectuent. Le respect de ces consignes de nommage permet une auto-documentation de vos packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . L'autre méthode permettant de documenter vos packages, consiste à utiliser des annotations. Pour plus d’informations sur les annotations, consultez [Utilisation des annotations dans les packages](use-annotations-in-packages.md).  
  
4.  Avec le bouton droit de la tâche de flux de données, cliquez sur **propriétés**, puis dans la fenêtre Propriétés, vérifiez que le `LocaleID` propriété est définie sur **anglais (États-Unis)**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Étape 5 : Ajout et configuration de la source de fichier plat](lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
## <a name="see-also"></a>Voir aussi  
 [tâche de flux de données](control-flow/data-flow-task.md)  
  
  
