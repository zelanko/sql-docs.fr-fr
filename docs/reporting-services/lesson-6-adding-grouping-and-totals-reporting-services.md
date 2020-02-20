---
title: 'Leçon 6 : Ajouter un regroupement et des totaux (Reporting Services) | Microsoft Docs'
ms.date: 04/18/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: e3d61228-2aa4-42cc-955e-602dbf3406a7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b5b9846a20615cf613dd50752ac63f2669b1e399
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "65089662"
---
# <a name="lesson-6-adding-grouping-and-totals-reporting-services"></a>Leçon 6 : Ajout d'un regroupement et de totaux (Reporting Services)

Dans la dernière leçon du tutoriel, vous allez ajouter un regroupement et des totaux à votre rapport [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour organiser et synthétiser vos données.  

## <a name="to-group-data-in-a-report"></a>Pour regrouper des données dans un rapport

1. Sélectionnez l’onglet **Conception**.
2. Si vous ne voyez pas le volet **Groupes de lignes**, cliquez avec le bouton droit sur l’aire de conception et sélectionnez **Vue** >**Regroupement**.
3. Faites glisser le champ `[Date]` du volet **Données du rapport** vers le volet **Groupes de lignes**. Placez-le au-dessus de la ligne **= (Details)** .

    > [!NOTE]
    > Notez que la poignée de ligne comporte maintenant un crochet, qui indique un groupe. De plus, le tableau présente désormais deux colonnes d’expression `[Date]`, placées de part et d’autre d’une ligne verticale en pointillé.
    >
    >![date d’ajout du groupe](media/rs-basictablegroups1design.png "date d’ajout du groupe")
4. Faites glisser le champ `[Order]` du volet **Données du rapport** vers le volet **Groupes de lignes**. Placez-le au-dessous du champ **Date** et au-dessus de la ligne **= (Details)** .

    ![ssrs_ssdt_addorderfield](media/ssrs-ssdt-addorderfield.png)

    > [!NOTE]
    > Notez que la poignée de ligne comporte maintenant deux crochets pour indiquer deux groupes ![ssrs_ssdt_rowgroupdoublehandles](media/ssrs-ssdt-rowgroupdoublehandles.png). Le tableau contient aussi désormais deux colonnes d’expression `[Order]`.

5. Supprimez les colonnes d’expression `[Date]` et `[Order]` d’origine à droite du double trait. Sélectionnez les poignées des deux colonnes, cliquez avec le bouton droit et sélectionnez **Supprimer les colonnes**. Le Concepteur de rapports supprime les expressions de ligne, afin que seules les expressions de groupe soient affichées.

    ![Sélectionner les colonnes à supprimer](media/rs-basictablegroupsdeletecols.gif "Sélectionner les colonnes à supprimer")

6. Pour mettre en forme la nouvelle colonne `[Date]`, cliquez avec le bouton droit dans la cellule de région de données qui contient l’expression `[Date]`, puis sélectionnez **Propriétés de la zone de texte**.
7. Sélectionnez **Nombre** dans la zone de liste de la colonne la plus à gauche, et **Date** dans la zone de liste **Catégorie**.
8. Dans la zone de liste **Type**, sélectionnez **January 31, 2000**.
9. Sélectionnez **OK** pour appliquer le format.
10. Affichez un aperçu du rapport. Il doit ressembler à ce qui suit :

    ![rs_BasicTableGroupsPreview](media/rs-basictablegroupspreview.png)

## <a name="adding-totals-to-a-report"></a>Ajoute de totaux à un rapport

1. Basculez en mode **Conception**.
2. Cliquez avec le bouton droit dans la cellule de région de données qui contient l’expression `[LineTotal]`, puis sélectionnez **Ajouter un total**. Le Concepteur de rapports ajoute une ligne avec la somme des montants en dollars de chaque commande.
3. Cliquez avec le bouton droit dans la cellule qui contient le champ `[Qty]`, puis sélectionnez **Ajouter un total**. Le Concepteur de rapports ajoute la somme des quantités de chaque commande à la ligne des totaux.
4. Dans la cellule vide à gauche de la cellule `Sum[Qty]`, tapez la chaîne « Total des commandes ».
5. Vous pouvez ajouter une couleur d'arrière-plan à la ligne des totaux. Sélectionnez les deux cellules de somme et la cellule d'étiquette.  
6. Dans le menu **Format**, sélectionnez **Couleur d’arrière-plan** > **Gris clair**.
7. Sélectionnez **OK** pour appliquer le format.

   ![Mode Conception : Table de base avec total des commandes](media/rs-basictablesumlinetotaldesign.gif "Mode Conception : Table de base avec total des commandes")

## <a name="add-the-daily-total-to-the-report"></a>Ajouter le total quotidien au rapport

1. Cliquez avec le bouton droit dans la cellule d’expression `[Order]`, puis sélectionnez **Ajouter un Total** > **Après**. Le Concepteur de rapports ajoute une nouvelle ligne contenant les sommes des valeurs `[Qty]` et `[Linetotal]` pour chaque jour, et la chaîne « Total » en bas de la colonne d’expression `[Order]`.
2. Tapez le mot « quotidien » après le mot « Total » dans la même cellule. Vous obtenez « Total quotidien ».
3. Sélectionnez cette cellule, les deux cellules de totaux adjacentes situées à droite et la cellule vide située entre elles.
4. Dans le menu **Format**, sélectionnez **Couleur d’arrière-plan** > **Orange**.
5. Sélectionnez **OK** pour appliquer le format.

   ![Définir la couleur d’arrière-plan sur orange](media/rs-basictablesumdaytotaldesign.gif "rs_BasicTableSumDayTotalDesign")

## <a name="add-the-grand-total-to-the-report"></a>Ajouter le total général au rapport

1. Cliquez avec le bouton droit dans la cellule d’expression `[Date]`, puis sélectionnez **Ajouter un Total** > **Après**. Le Concepteur de rapports ajoute une nouvelle ligne contenant les sommes des valeurs `[Qty]` et `[LineTotal]` pour le rapport entier, et la chaîne « Total » en bas de la colonne d’expression `[Date]`.
2. Tapez la chaîne « général » après le mot « Total » dans la même cellule. Vous obtenez « Total général ».
3. Sélectionnez la cellule qui contient « Total général », les deux cellules d’expression `Sum()` et les cellules vides situées entre elles.
4. Dans le menu **Format**, sélectionnez **Couleur d’arrière-plan** > **Bleu clair**.
5. Sélectionnez **OK** pour appliquer le format.

    ![Mode Conception : Total général dans une table de base](media/rs-basictablesumgrandtotaldesign.gif "Mode Conception : Total général dans une table de base")

## <a name="preview-the-report"></a>Afficher un aperçu du rapport

Pour afficher un aperçu des modifications de mise en forme, sélectionnez l’onglet **Aperçu**. Dans la barre d’outils **Aperçu**, sélectionnez le bouton **Dernière page**, qui ressemble à ![ssrs_ssdt_viewertoolbar_lastpage](media/ssrs-ssdt-viewertoolbar-lastpage.png). Les résultats affichés doivent ressembler à ceci :

   ![Préversion : Table de base avec total général](media/rs-basictablesumgrandtotalpreview.gif "Aperçu : Table de base avec total général")

## <a name="publishing-the-report-to-the-report-server-optional"></a>Publication du rapport sur le *Serveur de rapports* (facultatif)

Une étape facultative consiste à publier le rapport terminé sur le serveur de rapports afin de pouvoir le consulter dans le portail web.

1. Sélectionnez le menu **Projet** > **Propriétés de Tutorial**.
2. Dans **TargetServerURL**, tapez le nom de votre serveur de rapports, par exemple
    - `http:/<servername>/reportserver` ou
    - `https://localhost/reportserver` fonctionne si vous concevez le rapport sur le serveur de rapports.

3. **TargetReportFolder** a pour valeur Tutorial, le nom du projet. Le Concepteur de rapports déploie le rapport dans ce dossier.
4. Sélectionnez **OK**.
5. Sélectionnez le menu **Générer** > **Déployer Tutorial**.

    Si vous voyez un message semblable à ce qui suit dans la fenêtre **Sortie**, c’est que le déploiement a réussi.

    > ------ Build démarrée : Project: tutorial, Configuration: Debug ------  
    > 'Sales Orders.rdl' ignoré. L’élément est à jour.  
    > Fin de la génération -- 0 erreur, 0 avertissement  
    > ------ Deploy started: Project: tutorial, Configuration: Debug ------  
    > Déploiement vers `https://[server name]/reportserver`  
    > Déploiement du rapport '/tutorial/Sales Orders'.  
    > Fin du déploiement -- 0 erreur, 0 avertissement  
    > ========== Build : 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    > ========== Deploy: 1 réussi, 0 échoué, 0 ignoré ==========  

    Si un message d’erreur semblable au suivant s’affiche, vérifiez que vous disposez des autorisations appropriées sur le serveur de rapports et que vous avez démarré [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] avec des privilèges d’administrateur.
    >
    > Les autorisations accordées à l’utilisateur « XXXXXXXX\\[votre nom d’utilisateur] » ne sont pas suffisantes pour effectuer cette opération. »

6. Ouvrez un navigateur avec des privilèges d’administrateur. Par exemple, cliquez sur l’icône Internet Explorer et sélectionnez **Exécuter en tant qu’administrateur**.
7. Accédez à l’URL du portail web.
   - `https://<server name>/reports`.
   - `https://localhost/reports` fonctionne si vous concevez le rapport sur le serveur de rapports.

8. Sélectionnez le dossier Tutorial, puis sélectionnez le rapport « Sales Orders » pour afficher le rapport.

    ![ssrs_tutorial_tutorialfolder](media/ssrs-tutorial-tutorialfolder.png)  

Vous avez correctement mené à terme le tutoriel de **création d’un rapport de tableau de base**.

## <a name="see-also"></a>Voir aussi

[Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)
