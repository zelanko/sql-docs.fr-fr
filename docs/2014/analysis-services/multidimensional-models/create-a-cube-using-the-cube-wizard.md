---
title: Créer un cube à l’aide de l’Assistant Cube | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], creating
ms.assetid: d46d659c-3a4e-4364-94ac-f5eb6ba0ec25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7ffd5880120184249d89c4d702b30c8d6e01e1f6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66076503"
---
# <a name="create-a-cube-using-the-cube-wizard"></a>Créer un cube à l'aide de l'Assistant Cube
  Vous pouvez créer un cube en utilisant l’Assistant Cube dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
### <a name="to-create-a-new-cube"></a>Pour créer un cube  
  
1.  Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **cubes**, puis cliquez sur **Nouveau Cube**.  
  
2.  Dans la page **Sélectionner la méthode de création** de l’Assistant Cube, sélectionnez **Utiliser des tables existantes**, puis cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  Parfois, vous devez éventuellement créer un cube sans utiliser de tables existantes. Pour créer un cube vide, sélectionnez **Créer un cube vide**. Pour générer des tables, sélectionnez **Générer des tables dans la source de données**.  
  
3.  Dans la page **Sélectionner les tables de groupes de mesures** , suivez les procédures ci-dessous :  
  
    1.  Dans la liste **Vue de source de données** , sélectionnez une vue de source de données.  
  
    2.  Dans la liste **Tables de groupes de mesures** , sélectionnez les tables qui à utiliser pour créer des groupes de mesures.  
  
    3.  Cliquez sur **Suivant**.  
  
4.  Dans la page **Sélectionner les mesures** , sélectionnez les mesures à inclure dans le cube, puis cliquez sur **Suivant**.  
  
     Vous pouvez éventuellement modifier les noms des mesures et groupes de mesures.  
  
5.  Dans la page **Sélectionner des dimensions existantes** , sélectionnez les dimensions existantes à inclure dans le cube, puis cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  La page **Sélectionner des dimensions existantes** apparaît si des dimensions existent déjà dans la base de données pour les groupes de mesures sélectionnés.  
  
6.  Dans la page **Sélectionner de nouvelles dimensions** , sélectionnez les nouvelles dimensions à créer, puis cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  La page **Sélectionner de nouvelles dimensions** apparaît si des tables conviennent aux tables de dimension et si elles n’ont pas déjà été utilisées par des dimensions existantes.  
  
7.  Dans la page **Sélectionner les clés de dimension manquantes** , sélectionnez une clé pour la dimension, puis cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  La page **Sélectionner les clés de dimension manquantes** apparaît si une clé n’est pas définie pour une table de dimension que vous avez spécifiée.  
  
8.  Dans la page **Fin de l’Assistant** , entrez le nom du nouveau cube et examinez sa structure. Si vous souhaitez apporter des modifications, cliquez sur **Précédent**; sinon, cliquez sur **Terminer**.  
  
    > [!NOTE]  
    >  Vous pouvez utiliser le Concepteur de cube une fois l'exécution de l'Assistant Cube terminée pour définir le cube. Vous pouvez également utiliser le Concepteur de dimensions pour ajouter, supprimer et configurer des attributs et des hiérarchies dans les dimensions que vous avez créées.  
  
  
