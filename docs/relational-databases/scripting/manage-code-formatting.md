---
title: "G&#233;rer la mise en forme du code | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mise en retrait du code [SQL Server]"
  - "affichage des URL"
  - "mise en forme du code [SQL Server Management Studio]"
  - "réduction du texte"
  - "formats [SQL Server], mise en forme du code dans SQL Server Management Studio"
  - "masquage du texte"
  - "formats [SQL Server]"
  - "texte [SQL Server], formats de code"
  - "mise en retrait automatique"
  - "conversion du texte en caractères minuscules"
  - "Éditeur de requête [SQL Server Management Studio], gestion des formats de code"
  - "URL affichée dans du code [SQL Server Management Studio]"
  - "conversion du texte en caractères majuscules"
  - "texte [SQL Server]"
  - "annulation de la mise en retrait du code"
ms.assetid: ddbac4d2-6bdc-4467-a352-e869ec880eed
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# G&#233;rer la mise en forme du code
  Dans l'éditeur, vous pouvez mettre en forme votre code avec des mises en retrait, du texte caché, des URL, etc. Vous pouvez également mettre en forme automatiquement votre code à l'aide de la fonction de mise en retrait intelligente.  
  
## Mise en retrait  
 Vous avez le choix entre trois styles de mise en retrait du texte. Vous pouvez également spécifier le nombre d'espaces correspondant à une mise en retrait ou une tabulation, et déterminer si l'Éditeur de code applique la mise en retrait au moyen de tabulations ou d'espaces.  
  
#### Pour choisir un style de mise en retrait  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Cliquez sur **Éditeur de texte**.  
  
3.  Cliquez sur le dossier, puis sélectionnez **Tous les langages** pour définir la mise en retrait pour tous les langages.  
  
4.  Cliquez sur **Tabulations**.  
  
5.  Cliquez sur l'une des options suivantes :  
  
    -   **None**. Le curseur se positionne au début de la ligne suivante.  
  
    -   **Bloc**. Le curseur aligne la ligne suivante sur la ligne précédente.  
  
    -   **Intelligente** (par défaut). Le service du langage détermine le style de mise en retrait approprié à utiliser.  
  
    > [!NOTE]  
    >  Certains langages n'offrent pas toutes ces options de mise en retrait.  
  
#### Pour modifier les paramètres des tabulations de mise en retrait  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Cliquez sur **Éditeur de texte**.  
  
3.  Sélectionnez le dossier pour **Tous les langages** pour définir la mise en retrait pour tous les langages.  
  
4.  Cliquez sur **Tabulations**.  
  
5.  Pour spécifier des caractères de tabulation pour les opérations de tabulation et de mise en retrait, cliquez sur **Conserver les tabulations**. Pour spécifier des espaces, sélectionnez **Insérer des espaces**.  
  
     Si vous sélectionnez **Insérer des espaces**, vous pouvez entrer le nombre d’espaces représenté par chaque tabulation ou mise en retrait, respectivement sous **Taille des tabulations** ou **Taille du retrait**.  
  
#### Pour mettre du code en retrait  
  
1.  Sélectionnez le texte que vous souhaitez mettre en retrait.  
  
2.  Appuyez sur TAB ou cliquez sur le bouton **Retrait** dans la barre d’outils Standard.  
  
#### Pour annuler la mise en retrait du code  
  
1.  Sélectionnez le texte dont vous souhaitez annuler la mise en retrait.  
  
2.  Appuyez sur Maj+Tab ou cliquez sur le bouton **Annuler la mise en retrait** dans la barre d’outils Standard.  
  
#### Pour mettre automatiquement en retrait la totalité du code  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Cliquez sur **Éditeur de texte**.  
  
3.  Cliquez sur **Tous les langages**.  
  
4.  Cliquez sur **Tabulations**.  
  
5.  Cliquez sur **Intelligente**.  
  
> [!NOTE]  
>  L’option **Intelligente** n’est pas disponible pour certains langages.  
  
#### Pour convertir un espace en tabulations  
  
1.  Sélectionnez le texte qui contient l'espace que vous souhaitez convertir en tabulations.  
  
2.  Dans le menu **Edition**, pointez sur **Avancée**, puis cliquez sur **Remplacer les espaces par des tabulations**.  
  
#### Pour convertir des tabulations en espaces  
  
1.  Sélectionnez le texte qui contient les tabulations que vous souhaitez convertir en espaces.  
  
2.  Dans le menu **Edition**, pointez sur **Avancée**, puis cliquez sur **Remplacer les tabulations par des espaces**.  
  
 Le comportement de ces commandes dépend des paramètres de tabulation définis dans la boîte de dialogue **Options**. Par exemple, si le paramètre de tabulation a pour valeur quatre, **Remplacer les espaces par des tabulations** crée une tabulation pour tout groupe de quatre espaces contigus alors que **Remplacer les tabulations par des espaces** crée quatre espaces pour chaque tabulation.  
  
## Conversion de texte en majuscules et en minuscules  
 Des commandes vous permettent de convertir du texte en majuscules ou en minuscules.  
  
#### Pour convertir du texte en majuscules ou minuscules  
  
1.  Sélectionnez le texte à convertir.  
  
2.  Pour convertir du texte en majuscules, appuyez sur Ctrl+Maj+U ou cliquez sur **Mettre en majuscules** dans le sous-menu **Avancée** du menu **Edition**.  
  
3.  Pour convertir du texte en minuscules, appuyez sur Ctrl+Maj+L ou cliquez sur **Mettre en minuscules** dans le sous-menu **Avancée** du menu **Edition**.  
  
> [!NOTE]  
>  Pour obtenir la liste complète des touches de raccourci clavier, consultez [Raccourcis clavier dans SQL Server Management Studio](../../tools/sql-server-management-studio/sql-server-management-studio-keyboard-shortcuts.md).  
  
## Affichage et liaison à des URL  
 Vous pouvez créer et gérer des URL interactives dans votre code. Par défaut, les URL :  
  
-   sont soulignées ;  
  
-   entraînent la transformation du pointeur de la souris en une main lorsque vous passez par-dessus ;  
  
-   ouvrent le site correspondant lorsque vous cliquez une fois dessus, pour autant que l'URL soit valide.  
  
#### Pour afficher une URL interactive  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Cliquez sur **Éditeur de texte**.  
  
3.  Pour modifier l’option pour un seul langage, cliquez sur le dossier de celui-ci, puis sur **Général**. Pour modifier l’option pour tous les langages, cliquez sur **Tous les langages**, puis sur **Général**.  
  
4.  Sélectionnez **Activer la navigation dans les URL par simple clic**.  
  
  