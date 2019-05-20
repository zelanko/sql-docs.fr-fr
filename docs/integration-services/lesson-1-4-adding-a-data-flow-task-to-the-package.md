---
title: 'Étape 4 : Ajouter une tâche de flux de données au package | Microsoft Docs'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 96af3073-8f11-4444-b934-fe8613a2d084
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d0572019dabc6d62a634022ebeac2cdcb295a9e1
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65723332"
---
# <a name="lesson-1-4-add-a-data-flow-task-to-the-package"></a>Leçon 1-4 : Ajouter une tâche de flux de données au package

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Après avoir créé des gestionnaires de connexions pour les données sources et de destination, ajoutez une tâche de flux de données à votre package. La tâche de flux de données définit le moteur de flux de données qui déplace les données entre les sources et les destinations et fournit la fonctionnalité grâce à laquelle il est possible de transformer, nettoyer et modifier les données lors de leur déplacement. La tâche de flux de données est l'endroit où s'effectue la majorité du travail d'un processus d'extraction, de transformation et de chargement (ETL).  
  
> [!NOTE]  
> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sépare le flux de données du flux de contrôle.  
  
## <a name="add-a-data-flow-task"></a>Ajouter une tâche de flux de données  
  
1.  Sélectionnez l'onglet **Flux de contrôle**.  
  
2.  Dans le volet **Boîte à outils SSIS**, développez **Favoris** puis faites glisser une **Tâche de flux de données** sur l'aire de conception de l'onglet **Flux de contrôle**.  
  
    > [!NOTE]  
    > Si la boîte à outils SSIS n’est pas disponible, sélectionnez le menu **SSIS**, puis choisissez **Boîte à outils SSIS** pour afficher cette dernière.  

3.  Dans la zone de conception **Flux de contrôle**, cliquez avec le bouton droit sur la nouvelle **tâche de flux de données**, sélectionnez **Renommer** et changez le nom en **Extract Sample Currency Data**.  
  
    Affectez des noms uniques à tous les composants que vous ajoutez à une zone de conception. Afin d'utiliser et de maintenir les composants plus facilement, il est conseillé de leur affecter des noms décrivant leur fonction. Le respect de ces consignes de nommage permet une auto-documentation de vos packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . L'autre méthode permettant de documenter vos packages, consiste à utiliser des annotations. Pour plus d’informations sur les annotations, consultez [Utilisation des annotations dans les packages](../integration-services/use-annotations-in-packages.md).  
  
4.  Cliquez avec le bouton droit sur la tâche de flux de données, sélectionnez **Propriétés** puis, dans la fenêtre Propriétés, vérifiez que la propriété **LocaleID** est définie sur **Anglais (États-Unis)**.  
  
## <a name="go-to-next-task"></a>Passer à la tâche suivante
[Étape 5 : Ajouter et configurer la source du fichier plat](../integration-services/lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
## <a name="see-also"></a>Voir aussi  
[Tâche de flux de données](../integration-services/control-flow/data-flow-task.md)  
  
  
  
