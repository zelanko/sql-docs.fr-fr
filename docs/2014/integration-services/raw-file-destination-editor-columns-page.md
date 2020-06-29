---
title: Éditeur de destination de fichier brut (page colonnes) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledestinationcolumns.f1
ms.assetid: 37f61d0b-1269-42ee-94ab-011cbaac63e9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a0ceb00767715c3f0b5d149ecd7c8ac3116cf78
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85423206"
---
# <a name="raw-file-destination-editor-columns-page"></a>Éditeur de destination de fichier brut (page Colonnes)
  Utilisez l'Éditeur de destination de fichier brut pour configurer la destination de fichier brut et écrire des données brutes dans un fichier.  
  
 **Que voulez-vous faire ?**  
  
-   [Ouvrir l’éditeur de destination de fichier brut](#open)  
  
-   [Définir les options de l’onglet Gestionnaire de connexions](#connection)  
  
-   [Définir les options de l'onglet Colonnes](#mapping)  
  
##  <a name="open-the-raw-file-destination-editor"></a><a name="open"></a> Ouvrir l'Éditeur de destination de fichier brut  
  
1.  Ajoutez la destination de fichier brut à un package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
2.  Cliquez avec le bouton droit sur le composant, puis cliquez sur **Modifier**.  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a> Définir les options de l'onglet Gestionnaires de connexions  
 **Mode d’accès**  
 Sélectionnez la façon dont le nom de fichier est spécifié. Sélectionnez **Nom de fichier** pour entrer directement le nom de fichier et le chemin d'accès, ou bien **Nom de fichier à partir d'une variable** pour spécifier une variable qui contient le nom de fichier.  
  
 **Nom de fichier** ou **Nom de la variable**  
 Entrez le nom et le chemin d'accès du fichier brut, ou sélectionnez la variable contenant le nom du fichier.  
  
 **Option d'écriture**  
 Sélectionnez la méthode utilisée pour créer le fichier et y écrire.  
  
 **Générer le fichier brut initial**  
 Cliquez sur le bouton pour générer un fichier brut vide qui contient uniquement les colonnes (fichier réservé aux métadonnées), sans avoir à exécuter le package. Vous pouvez faire pointer la source de fichier brut vers le fichier réservé aux métadonnées.  
  
 Lorsque vous cliquez sur le bouton, la liste des colonnes s'affiche. Vous pouvez cliquer sur Annuler et modifier les colonnes, ou vous pouvez cliquer sur OK pour continuer à créer le fichier.  
  
##  <a name="set-options-on-the-columns-tab"></a><a name="mapping"></a>Définir les options de l’onglet colonnes  
 **Colonnes d’entrée disponibles**  
 Sélectionnez une ou plusieurs colonnes d'entrée pour écrire dans le fichier brut.  
  
 **Colonne d'entrée**  
 Une colonne d’entrée est automatiquement ajoutée à cette table quand vous la sélectionnez sous **Colonnes d’entrée disponibles**. Vous pouvez également sélectionner directement la colonne d’entrée dans cette table.  
  
 **Alias de sortie**  
 Spécifiez un autre nom pour la colonne de sortie.  
  
## <a name="see-also"></a>Voir aussi  
 [Destination de fichier brut](data-flow/raw-file-destination.md)  
  
  
