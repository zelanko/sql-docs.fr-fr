---
title: "Éditeur de Destination de fichier brut (Page Gestionnaire de connexions) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.rawfiledestinationconnectionmanager.f1
ms.assetid: a0ec9643-3b44-4467-b855-f45ae4794f7f
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9f27180b2dca144905af1a5346d3d8747aa8248a
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="raw-file-destination-editor-connection-manager-page"></a>Éditeur de destination de fichier brut (page Gestionnaire de connexions)
  Utilisez l'Éditeur de destination de fichier brut pour configurer la destination de fichier brut et écrire des données brutes dans un fichier.  
  
 **Que voulez-vous faire ?**  
  
-   [Ouvrir l'Éditeur de destination de fichier brut](#open)  
  
-   [Définir les options de l'onglet Gestionnaires de connexions](#connection)  
  
-   [Définir les options de l'onglet Colonnes](#mapping)  
  
##  <a name="open"></a> Ouvrir l'Éditeur de destination de fichier brut  
  
1.  Ajoutez la destination de fichier brut à un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Cliquez avec le bouton droit sur le composant, puis cliquez sur **Modifier**.  
  
##  <a name="connection"></a> Définir les options de l'onglet Gestionnaires de connexions  
 **Mode d'accès**  
 Sélectionnez la façon dont le nom de fichier est spécifié. Sélectionnez **Nom de fichier** pour entrer directement le nom de fichier et le chemin d'accès, ou bien **Nom de fichier à partir d'une variable** pour spécifier une variable qui contient le nom de fichier.  
  
 **Nom de fichier** ou **Nom de la variable**  
 Entrez le nom et le chemin d'accès du fichier brut, ou sélectionnez la variable contenant le nom du fichier.  
  
 **Option d'écriture**  
 Sélectionnez la méthode utilisée pour créer le fichier et y écrire.  
  
 **Générer le fichier brut initial**  
 Cliquez sur le bouton pour générer un fichier brut vide qui contient uniquement les colonnes (fichier réservé aux métadonnées), sans avoir à exécuter le package. Le fichier contient les colonnes sélectionnées à la page **Colonnes** de la boîte de dialogue **Éditeur de destination de fichier brut**. Vous pouvez faire pointer la source de fichier brut vers ce fichier réservé aux métadonnées.  
  
 Lorsque vous cliquez sur **Générer le fichier brut initial**, un message s'affiche. Cliquez sur **OK** pour commencer la création du fichier. Cliquez sur **Annuler** pour sélectionner une autre liste de colonnes sur la page **Colonnes** .  
  
##  <a name="mapping"></a> Définir les options de l'onglet Colonnes  
 **Colonnes d'entrée disponibles**  
 Sélectionnez une ou plusieurs colonnes d'entrée pour écrire dans le fichier brut.  
  
 **Colonne d'entrée**  
 Une colonne d’entrée est automatiquement ajoutée à cette table quand vous la sélectionnez sous **Colonnes d’entrée disponibles**. Vous pouvez également sélectionner directement la colonne d’entrée dans cette table.  
  
 **Alias de sortie**  
 Spécifiez un autre nom pour la colonne de sortie.  
  
## <a name="see-also"></a>Voir aussi  
 [Destination de fichier brut](../../integration-services/data-flow/raw-file-destination.md)  
  
  
