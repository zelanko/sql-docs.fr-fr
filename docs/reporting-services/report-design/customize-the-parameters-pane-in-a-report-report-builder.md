---
title: Personnaliser le volet Paramètres dans un rapport (Générateur de rapports) | Microsoft Docs
description: Découvrez comment personnaliser le volet Paramètres lors de la création de rapports paginés avec des paramètres dans le Générateur de rapports.
ms.date: 06/15/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 4ce9e8d5-911a-4422-928f-a8d005b79fc6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 29bd397d64280644394077a29a3420dbf43b5e6f
ms.sourcegitcommit: 7d6eb09588ff3477cf39a8fd507d537a603bc60d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84796560"
---
# <a name="customize-the-parameters-pane-in-a-report-report-builder"></a>Customize the Parameters Pane in a Report (Report Builder)
  Lors de la création de rapports paginés avec des paramètres dans le Générateur de rapports, vous pouvez personnaliser le volet Paramètres. Dans la vue Conception de rapport, vous pouvez faire glisser un paramètre vers une colonne et une ligne spécifiques du volet Paramètres. Vous pouvez ajouter et supprimer des colonnes pour modifier la disposition du volet.

 Quand vous faites glisser un paramètre vers une nouvelle colonne et une nouvelle ligne du volet, l’ordre des paramètres change dans le volet **Données du rapport** . Quand vous modifiez l’ordre du paramètre dans le volet **Données du rapport** , ce paramètre change d’emplacement dans le volet. Pour plus d’informations sur les raisons pour lesquelles l’ordre des paramètres est important, consultez [Modifier l’ordre d’un paramètre de rapport &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md).

## <a name="to-customize-the-parameters-pane"></a>Pour personnaliser le volet Paramètres

1.  Dans l’onglet **Affichage** , cochez la case **Paramètres** pour afficher le volet Paramètres.

     ![Volet Paramètres d’accès à partir de l’onglet Affichage](../../reporting-services/report-design/media/ssrs-customparameter-accessparameterpanedesignmode.png "Volet Paramètres d’accès à partir de l’onglet Affichage")

     Le volet apparaît dans la partie supérieure de l’aire de conception.

2.  Pour ajouter un paramètre au volet, effectuez l’une des opérations suivantes.

    -   Cliquez avec le bouton droit sur une cellule vide du volet Paramètres et sélectionnez **Ajouter un paramètre**.

         ![Ajouter un nouveau paramètre à partir du volet Paramètres](../../reporting-services/report-design/media/ssrs-customizeparameter-addnewparameter.png "Ajouter un nouveau paramètre à partir du volet Paramètres")

    -   Dans le volet **Paramètres** , cliquez avec le bouton droit sur **Données du rapport** et sélectionnez **Ajouter un paramètre**.

3.  Pour déplacer un paramètre au sein du volet Paramètres, faites glisser le paramètre vers une autre cellule du volet.

     Lorsque vous modifiez l’emplacement du paramètre dans le volet, l’ordre de ce paramètre dans la liste **Paramètres** du volet **Données du rapport** change automatiquement. Pour plus d’informations sur l’impact de l’ordre des paramètres, consultez [Modifier l’ordre d’un paramètre de rapport &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)

4.  Pour accéder aux propriétés d’un paramètre, effectuez l’une des opérations suivantes.

    -   Cliquez avec le bouton droit sur le paramètre dans le volet Paramètres et sélectionnez **Propriétés du paramètre**.

         ![Accéder aux propriétés du paramètre à partir du volet Paramètres](../../reporting-services/report-design/media/ssrs-customizeparameter-accessparameterproperties-composite.png "Accéder aux propriétés du paramètre à partir du volet Paramètres")

    -   Cliquez avec le bouton droit sur le paramètre dans le volet **Données du rapport** et sélectionnez **Propriétés du paramètre**.

5.  Pour ajouter des colonnes et des lignes au volet ou pour supprimer des colonnes et lignes existantes, cliquez avec le bouton droit sur un emplacement quelconque du volet Paramètres et sélectionnez la commande appropriée dans le menu qui s’affiche.

     ![Ajouter des colonnes et des lignes au volet Paramètres](../../reporting-services/report-design/media/ssrs-customparameter-addcolumnsrows.png "Ajouter des colonnes et des lignes au volet Paramètres")

    > [!IMPORTANT]
    >  Quand vous supprimez une colonne ou une ligne contenant des paramètres, ces paramètres sont supprimés du rapport.

6.  Pour supprimer un paramètre du volet et du rapport, effectuez l’une des opérations suivantes.

    -   Cliquez avec le bouton droit sur le paramètre dans le volet Paramètres et sélectionnez  **Supprimer**.

         ![Supprimer des paramètre dans le volet Paramètres](../../reporting-services/report-design/media/ssrs-customparameter-deleteparameter.png "Supprimer des paramètre dans le volet Paramètres")

    -   Cliquez avec le bouton droit sur le paramètre dans le volet **Données du rapport** et sélectionnez **Supprimer**.

## <a name="hiddeninternal-parameters-during-runtime"></a>Paramètres masqués/internes lors de l’exécution
Si vous avez un paramètre masqué/interne, la logique qui détermine s’il s’affiche sous la forme d’un espace vide pendant l’exécution est la suivante :

   - Si une ligne ou une colonne ne contient que des paramètres masqués/internes ou des cellules vides, la totalité de la ligne ou de la colonne ne s’affiche pas au cours de l’exécution
   - Sinon, le paramètre masqué/interne ou la cellule vide est affiché sous la forme d’un espace vide

Par exemple, `ReportParameter1` est masqué tandis que les autres paramètres sont visibles :

![Paramètre masqué - Exemple 1](../../reporting-services/report-design/media/ssrs-hidden-parameter-rb-1.png "Un paramètre masqué dans la grille de disposition")

Le résultat est un espace vide lors de l’exécution, car il existe des paramètres visibles dans la première colonne ou la première ligne :

![Paramètre masqué - Exemple 1 - Exécution](../../reporting-services/report-design/media/ssrs-hidden-parameter-server-1.png "Un paramètre masqué dans la grille de disposition se traduit par un espace vide lors de l’exécution")

En utilisant le même exemple, si vous définissez également `ReportParameter3` comme masqué :

![Paramètre masqué - Exemple 2](../../reporting-services/report-design/media/ssrs-hidden-parameter-rb-2.png "Deux paramètres masqués dans la même colonne")

La première colonne n’est alors pas affichée au moment de l’exécution, car la colonne entière est considérée comme vide :

![Paramètre masqué - Exemple 2 - Exécution](../../reporting-services/report-design/media/ssrs-hidden-parameter-server-2.png "Deux paramètres masqués dans la même colonne lors de l’exécution")

## <a name="default-layout"></a>Disposition par défaut
Pour les rapports qui ont été créés avant SQL Server Reporting Services 2016, une grille de disposition de paramètres par défaut de 2 colonnes et N lignes est utilisée lors de l’exécution. Pour changer la disposition par défaut, ouvrez le rapport Microsoft Report Builder et enregistrez le rapport. Une fois le rapport enregistré, les informations sur la mise en page personnalisée des paramètres sont enregistrées dans le fichier .rdl.


## <a name="see-also"></a>Voir aussi
 [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)


