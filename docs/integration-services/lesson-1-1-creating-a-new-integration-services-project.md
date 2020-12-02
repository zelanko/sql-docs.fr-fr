---
description: 'Leçon 1-1 : Créer un projet Integration Services'
title: 'Étape 1 : Créer un projet Integration Services | Microsoft Docs'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: f14521b5-941e-443b-8f5e-385f98e37fbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 575353cd2cf770ed42d439fd31647ccaef3e01bd
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "88449747"
---
# <a name="lesson-1-1-create-a-new-integration-services-project"></a>Leçon 1-1 : Créer un projet Integration Services

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



La première étape de la création d'un package dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] consiste à créer un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Cet exemple de projet comprend les modèles des sources de données, vues de source de données et packages qui constituent une solution de transformation de données.  
  
Les packages que vous créez dans ce didacticiel [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] interprètent les valeurs des données de paramètres régionaux. Si votre ordinateur n'est pas configuré pour l'utilisation du paramètre **Anglais (États-Unis)**, vous devez définir des propriétés supplémentaires dans le package. 

Les packages que vous utilisez dans les leçons 2 à 6 sont copiés à partir du package que vous créez dans cette leçon.  
  
> [!NOTE]  
> Si ce n’est déjà fait, consultez les [prérequis de la leçon 1](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites).

## <a name="create-a-new-integration-services-project"></a>Créer un projet Integration Services  
  
1.  Dans le menu **Démarrer** de Windows, recherchez et sélectionnez **Visual Studio (SSDT)**.  
  
2.  Dans Visual Studio, sélectionnez **Fichier** > **Nouveau** > **Projet** pour créer un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
3.  Dans la boîte de dialogue **Nouveau projet** , développez le nœud **Business Intelligence** sous **Installé**, puis sélectionnez **Projet Integration Services** dans le volet **Modèles**.  
  
4.  Dans la zone **Nom** , remplacez le nom par défaut par **SSIS Tutorial**. Pour utiliser un dossier existant, désactivez la case à cocher **Créer un répertoire pour la solution**.  
  
5.  Acceptez l'emplacement par défaut ou sélectionnez **Parcourir** pour rechercher et accéder au dossier que vous souhaitez utiliser. Dans la boîte de dialogue **Emplacement du projet**, choisissez le dossier puis **Sélectionner le dossier**.  
  
6.  Sélectionnez **OK**.  
  
    Par défaut, un package vide nommé **Package.dtsx** est créé et ajouté à votre projet sous **Packages SSIS**.  
  
7.  Dans **l’Explorateur de solutions** , cliquez avec le bouton droit sur **Package.dtsx**, sélectionnez **Renommer**, puis attribuez au package par défaut le nom **Lesson 1.dtsx**.  
  
## <a name="go-to-next-task"></a>Passer à la tâche suivante
[Étape 2 : Ajouter et configurer un gestionnaire de connexions de fichiers plats](../integration-services/lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
