---
title: Importer un projet d’exploration de données à l’aide de l’Assistant Importation d’Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 62bc9fc5-c6ff-4517-b598-d92df76743a2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c34694012a69285ee92fa90c58f293654c961890
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62722351"
---
# <a name="import-a-data-mining-project-using-the-analysis-services-import-wizard"></a>Importer un projet d'exploration de données à l'aide de l'Assistant Importation d'Analysis Services
  Cette rubrique décrit la méthode de création d’un projet d’exploration de données en important les métadonnées d’un projet existant d’exploration de données sur un autre serveur, à l’aide du modèle **Importer à partir du serveur (Multidimensionnel et exploration de données)**, dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
## <a name="import-data-sources-mining-structures-and-mining-models-from-an-existing-data-mining-project"></a>Importez des sources de données, des structures d'exploration de données et des modèles d'exploration de données d'un projet existant d'exploration de données  
 Quand vous utilisez le modèle **Importer à partir du serveur (Multidimensionnel et exploration de données)**, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] crée un projet d’exploration de données, puis copie les métadonnées du projet d’exploration de données spécifié. Le nouveau projet contient les mêmes sources de données, vues de source de données, structures d'exploration de données et modèles d'exploration de données que la base de données ssASnoversion à partir de laquelle vous avez effectué l'importation. Toutefois, le projet ne peut pas être utilisé tant que certaines propriétés ne sont pas mises à jour et que les objets n'ont pas été traités comme suit :  
  
-   Les données proprement dites ne sont pas copiées à partir du serveur source pour l’exploration de données nouveau projet uniquement que les définitions des sources de données et les vues de sources de données sont importées. Par conséquent, une fois l'importation terminée et les objets créés, vous devez remplir les objets avec les données par apprentissage des structures d'exploration de données et des modèles dépendants. Vous pouvez utiliser la commande **Traiter tout** dans le Concepteur d'exploration de données pour effectuer l'apprentissage des modèles et des structures.  
  
-   Si vous importez un projet créé dans une version antérieure d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], la source de données peut utiliser les fournisseurs qui ne sont pas installés sur le serveur sur lequel vous importez le projet. Si vous rencontrez des erreurs lors du traitement des structures d’exploration de données importées, cliquez avec le bouton droit sur chaque source de données et sélectionnez **Ouvrir le concepteur** pour modifier la chaîne de connexion et vérifier les propriétés du fournisseur.  
  
     À ce stade, vous devrez peut-être aussi vérifier que le compte que vous utilisez pour traiter les objets d'exploration de données ou interroger les modèles d'exploration de données dispose des autorisations nécessaires sur la source de données.  
  
-   Par défaut, lorsque vous importez un projet, la base de données de l'espace de travail est définie sur localhost, ou quelque soit l'instance par défaut, elle est configurée comme **Serveur cible par défaut** dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Pour définir cette propriété, dans le menu **Options** , sélectionnez **Concepteurs Business Intelligence**, sélectionnez **Analysis Services**, puis sélectionnez **Général**.  
  
     Notez que, dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous pouvez définir une autre option séparée pour configurer le serveur de déploiement par défaut pour les projets de modèles tabulaires d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Le paramètre **Serveur de déploiement par défaut**détermine la base de données d'espace de travail par défaut des projets de modèles tabulaires. Vous ne pouvez pas utiliser les instances qui prennent en charge les modèles tabulaires pour les projets d'exploration de données  
  
     Si vous ne pouvez pas modifier la base de données de déploiement par défaut pour utiliser une instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] s'exécutant en mode multidimensionnel ou d'exploration de données, vous pouvez toujours spécifier la base de données de déploiement à l'aide de la boîte de dialogue **Propriétés du projet** .  
  
#### <a name="to-create-a-new-data-mining-project-by-importing-an-existing-data-mining-project"></a>Pour créer un nouveau projet d'exploration de données en important un projet d'exploration de données existant  
  
1.  Dans le menu [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]Fichier **de** , cliquez sur **Nouveau**, puis sur **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet** , sous **Modèles installés**, cliquez sur **Business Intelligence**sur **Analysis Services**, puis sur **Importer à partir du serveur (Multidimensionnel et exploration de données)**.  
  
3.  Pour le **Nom**, tapez un nom pour le projet, puis spécifiez un emplacement et le nom de la solution et cliquez sur **OK**.  
  
     L' **Assistant Importation de base de données Analysis Services** démarre. Cliquez sur OK dans la page d'accueil pour continuer.  
  
4.  Dans la page **Sélectionner la base de données source**, pour **Serveur**, spécifiez l'instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui contient la solution que vous souhaitez importer.  
  
     Pour **Base de données**, choisissez la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui contient les objets d'exploration de données que vous souhaitez importer.  
  
    > [!WARNING]  
    >  Vous ne pouvez pas spécifier les objets que vous souhaitez importer ; lorsque vous choisissez une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] existante, tous les objets multidimensionnels et d'exploration de données sont importés.  
  
     Cliquer sur **Suivant**.  
  
5.  La page **Fin de l'Assistant**affiche la progression de l'opération d'importation. Vous ne pouvez pas annuler l'opération ou modifier les objets qui sont importés. Cliquez sur **Terminer** lorsque vous avez terminé.  
  
     Le nouveau projet est automatiquement ouvert à l'aide de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de projet &#40;SSAS Tabulaire&#41;](../tabular-models/properties-ssas-tabular.md)  
  
  
