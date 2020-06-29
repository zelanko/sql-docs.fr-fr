---
title: 'Étape 1 : Création d’un projet Integration Services | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f14521b5-941e-443b-8f5e-385f98e37fbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c96b23a8807741429eaee00dace7c22f1cd540c5
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436226"
---
# <a name="step-1-creating-a-new-integration-services-project"></a>Étape 1 : Création d’un nouveau projet Integration Services
  La première étape de la création d'un package dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] consiste à créer un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Ce projet comprend les modèles des objets (sources de données, vues de source de données et packages) que vous utilisez dans une solution de transformation de données.  
  
 Les packages que vous allez créer dans ce didacticiel [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] interprètent les valeurs des données de paramètres régionaux. Si votre ordinateur n'est pas configuré pour l'utilisation du paramètre Anglais (États-Unis), vous devez définir des propriétés supplémentaires dans le package. Les packages que vous utilisez dans les leçons 2 à 5 sont copiés à partir du package créé dans la leçon 1 ; vous n'avez pas besoin de mettre à jour les propriétés des paramètres régionaux dans les packages copiés.  
  
> [!NOTE]  
>  Ce didacticiel nécessite Microsoft SQL Server Data Tools.  
>   
>  Pour plus d’informations sur l’installation de SQL Server Data Tools, consultez [Télécharger SSDT (SQL Server Data Tools)](https://msdn.microsoft.com/data/hh297027).  
  
### <a name="to-create-a-new-integration-services-project"></a>Pour créer un nouveau projet Integration Services  
  
1.  Dans le menu **Démarrer** , pointez sur **Tous les programmes**, puis sur **Microsoft SQL Server**et cliquez sur **SQL Server Data Tools**.  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet** pour créer un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
3.  Dans la boîte de dialogue **Nouveau projet** , développez le nœud **Business Intelligence** sous **Modèles installés**, puis sélectionnez **Projet Integration Services** dans le volet **Modèles** .  
  
4.  Dans la zone **Nom** , remplacez le nom par défaut par **SSIS Tutorial**. Vous pouvez éventuellement désactiver la case à cocher **Créer le répertoire pour la solution** .  
  
5.  Acceptez l'emplacement par défaut ou cliquez sur **Parcourir** pour rechercher et accéder au dossier que vous souhaitez utiliser. Dans la boîte de dialogue **Emplacement du projet** , cliquez sur le dossier, puis sur **Sélectionner le dossier**.  
  
6.  Cliquez sur **OK**.  
  
     Par défaut, un package vide nommé **Package.dtsx**est créé et ajouté à votre projet sous Packages SSIS.  
  
7.  Dans la barre d’outils de **l’Explorateur de solutions** , cliquez avec le bouton droit sur **Package.dtsx**, choisissez **Renommer**, puis attribuez au package par défaut le nom **Lesson 1.dtsx**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Étape 2 : Ajout et configuration d’un Gestionnaire de connexions de fichiers plats](lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
  
