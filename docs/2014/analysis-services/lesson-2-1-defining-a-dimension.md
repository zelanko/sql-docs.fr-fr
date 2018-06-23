---
title: Définition d’une Dimension | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 112696db-3838-4b50-91bd-d2ce5fa04ee5
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.openlocfilehash: df62cff6aa47c37371d6a3ad6f52f120ad3f740b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153820"
---
# <a name="defining-a-dimension"></a>Définition d'une dimension
  Dans la tâche suivante, vous allez utiliser l'Assistant Dimension pour générer une dimension Date.  
  
> [!NOTE]  
>  Avant de commencer cette leçon, vous devez avoir terminé toutes les procédures de la leçon 1.  
  
### <a name="to-define-a-dimension"></a>Pour définir une dimension  
  
1.  Dans l’Explorateur de solutions (à droite de Microsoft Visual Studio), cliquez avec le bouton droit sur **Dimensions**, puis cliquez sur **Nouvelle dimension**. L'Assistant Dimension apparaît.  
  
2.  Dans la page **Assistant Dimension** , cliquez sur **Suivant**.  
  
3.  Dans la page **Sélectionner la méthode de création** , vérifiez que l’option **Utiliser une table existante** est sélectionnée, puis cliquez sur **Suivant**.  
  
4.  Dans la page **Spécifier des informations sur la source** , vérifiez que la vue de source des données **Adventure Works DW 2012** est sélectionnée.  
  
5.  Dans la liste **Table principale** , sélectionnez **Date**.  
  
6.  Cliquez sur **Suivant**.  
  
7.  Dans la page **Sélectionner les attributs de la dimension** , cochez les cases à côté des attributs suivants :  
  
    -   **Date Key**  
  
    -   **Full Date Alternate Key**  
  
    -   **English Month Name**  
  
    -   **Calendar Quarter**  
  
    -   **Calendar Year**  
  
    -   **Calendar Semester**  
  
8.  Modifiez le paramètre de la colonne **Type d’attribut** de l’attribut **Full Date Alternate Key** de **Regular** en **Date**. Pour cela, cliquez sur **Regular** dans la colonne **Type d’attribut** . Puis, cliquez sur la flèche pour développer les options. Ensuite, cliquez sur **Date** > **Calendar** > **Date**. Cliquez sur **OK**. Répétez ces étapes pour modifier le type d’attribut des attributs suivants comme suit :  
  
    -   **English Month Name** en **Month**  
  
    -   **Calendar Quarter** en **Quarter**  
  
    -   **Calendar Year** en **Year**  
  
    -   **Calendar Semester** en **Half Year**  
  
9. Cliquez sur **Suivant**.  
  
10. Dans la page **Fin de l’Assistant** , dans le volet de visualisation, vous pouvez consulter la dimension **Date** et ses attributs.  
  
11. Cliquez sur **Terminer** pour terminer l’Assistant.  
  
     Dans l’Explorateur de solutions, dans le projet Didacticiel [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , la dimension Date apparaît dans le dossier **Dimensions** . Au centre de l'environnement de développement, le Concepteur de dimensions affiche la dimension Date.  
  
12. Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Définition d’un Cube](lesson-2-2-defining-a-cube.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Dimensions dans les modèles multidimensionnels](multidimensional-models/dimensions-in-multidimensional-models.md)   
 [Créer une Dimension à l’aide d’une Table existante](multidimensional-models/create-a-dimension-by-using-an-existing-table.md)   
 [Créer une dimension à l’aide de l’Assistant Dimension](multidimensional-models/create-a-dimension-using-the-dimension-wizard.md)  
  
  