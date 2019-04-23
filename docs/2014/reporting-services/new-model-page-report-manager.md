---
title: Page nouveau modèle (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 27d5bf66-b0e7-489e-a830-ffe2ec8e5350
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b0d571210c44026fc34ab43cb07e18bbd8526ed5
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59948575"
---
# <a name="new-model-page-report-manager"></a>Page Nouveau modèle (Gestionnaire de rapports)
  Utilisez cette page pour générer un modèle de rapport par défaut à partir d'une source de données partagée. Vous ne pouvez générer des modèles de rapport qu'à partir de sources de données multidimensionnelles [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , de sources de données relationnelles [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et de sources de données relationnelles Oracle.  
  
 Les modèles que vous générez dans le Gestionnaire de rapports sont basés sur le schéma de la source de données partagée. Les entités, dossiers et champs sont créés pour toutes les tables et colonnes dans la source de données. Vous ne pouvez pas exclure d'éléments, ni définir d'options qui déterminent la façon dont le modèle est généré. Si vous souhaitez personnaliser ou affiner un modèle, vous devez plutôt utiliser le Générateur de modèles.  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-new-model-page"></a>Pour ouvrir la page Nouveau modèle  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez la source de données partagée depuis laquelle vous souhaitez générer un modèle.  
  
2.  Pointez sur la source de données et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, effectuez l'une des étapes suivantes :  
  
    -   Cliquez sur **Générer le modèle de rapport** pour ouvrir la page Nouveau modèle.  
  
    -   Cliquez sur **Gérer** pour ouvrir la page des propriétés générales du rapport. Cliquez ensuite sur **Générer le modèle** pour ouvrir la page Nouveau modèle.  
  
## <a name="options"></a>Options  
 **Nom**  
 Spécifie le nom du modèle. Le nom doit contenir un caractère alphanumérique au minimum. Il peut également comporter des espaces et quelques symboles. N'utilisez pas les caractères suivants dans le nom :  
  
 ; ? : \@ & = + , $ / * \< > | " /  
  
 **Description**  
 Affiche une description du modèle. Les utilisateurs qui consultent cet élément par le biais du Gestionnaire de rapports affichent cette description en parcourant l'arborescence des dossiers.  
  
 **Modifier l’emplacement**  
 Affiche l'emplacement du dossier pour le nouveau modèle. Vous pouvez cliquer sur le bouton **Modifier l'emplacement** pour sélectionner un emplacement différent.  
  
  
