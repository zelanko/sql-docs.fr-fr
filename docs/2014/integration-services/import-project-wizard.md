---
title: Assistant Importation de projet | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ssis.importprojectwizard.f1
ms.assetid: 9247ad6c-4bd1-43ab-b347-583181cb9917
caps.latest.revision: 9
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2e25fd5e0d0142d7e29f14fc1691c979bac24149
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37314139"
---
# <a name="import-project-wizard"></a>Assistant Importation de projet
  Utilisez l'Assistant Importation de projet de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] pour créer un nouveau projet Integration Services en fonction d'un projet existant. Importez des projets déjà déployés dans le catalogue [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ou à partir d’un fichier de déploiement de projet (extension .ispac).  
  
### <a name="to-create-a-project-based-on-a-project-in-ispac-file-or-in-catalog"></a>Pour créer un projet basé sur un projet dans un fichier .ispac ou dans le catalogue  
  
1.  Cliquez sur **Fichier**, pointez sur **Nouveau**, puis cliquez sur Projet.  
  
2.  Développez **Business Intelligence**, puis cliquez sur **Integration Services**.  
  
3.  Sélectionnez **Assistant Importation de projet Integration Services** dans le volet central, tapez un **nom** pour la solution, le projet, puis spécifiez le **dossier** du projet et cliquez sur **OK**.  
  
     Vous devez voir l' **Assistant Importation de projet Integration Services**. Cet Assistant crée un nouveau projet Integration Services en fonction d'un projet existant  
  
4.  Cliquez sur **Suivant** sur la page **Introduction** pour afficher la page **Sélectionner une source** .  
  
5.  Spécifiez si vous souhaitez importer le projet à partir d'un fichier .ispac ou d'un catalogue.  
  
    -   Si vous sélectionnez l'option **Fichier de déploiement de projet** , spécifiez le chemin d'accès au fichier .ispac.  
  
    -   Si vous sélectionnez l'option **Catalogue Integration Services** , spécifiez le nom de l'instance du serveur de base de données sur laquelle le catalogue existe et le chemin d'accès au projet dans le catalogue.  
  
6.  Cliquez sur **Suivant** sur la page **Sélectionner une source** pour afficher la page **Révision** . Vérifiez les informations affichées dans la page concernant l'opération d'importation que l'Assistant va exécuter.  
  
7.  Cliquez sur **Importer** pour créer un nouveau projet Integration Services selon le projet sélectionné.  
  
8.  La page **Résultats** doit afficher les résultats de l'opération d'importation exécutée par l'Assistant. Cliquez sur **Enregistrer le rapport** pour enregistrer le rapport dans un fichier XML.  
  
9. Pour fermer l'Assistant, cliquez sur **Fermer** .  
  
  
