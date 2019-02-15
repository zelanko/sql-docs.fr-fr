---
title: 'Leçon 6 : Ajout de regroupement et totaux (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: e3d61228-2aa4-42cc-955e-602dbf3406a7
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5409938a5e859d5df6a153cddf327129b2ca8878
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56296897"
---
# <a name="lesson-6-adding-grouping-and-totals-reporting-services"></a>Leçon 6 : ajout d'un regroupement et de totaux (Reporting Services)
  Ajoutez un regroupement et des totaux à votre rapport pour organiser et synthétiser vos données.  
  
 Pour plus d'informations sur l'ajout de totaux cumulés à des rapports, consultez le site curah.microsoft.com : [Ajout de totaux à des rapports Reporting Services (SSRS)](https://go.microsoft.com/fwlink/p/?LinkId=403698).  
  
 **Dans cette rubrique :**  
  
-   [Pour regrouper les données dans un rapport](#bkmk_groupdata)  
  
-   [Pour ajouter des totaux à un rapport](#bkmk_addtotals)  
  
-   [Pour ajouter un total quotidien à un rapport](#bkmk_adddailytotal)  
  
-   [Pour ajouter un total général à un rapport](#bkmk_addgrandtotal)  
  
-   [Pour publier le rapport sur le serveur de rapports (facultatif)](#bkmk_publishreport)  
  
##  <a name="bkmk_groupdata"></a> Pour regrouper les données dans un rapport  
  
1.  Cliquez sur l'onglet **Conception** .  
  
2.  Si vous ne voyez pas le volet **Groupes de lignes** , cliquez avec le bouton droit sur l'aire de conception, puis sélectionnez **Vue** et cliquez sur **Regroupement**.  
  
3.  À partir de la **les données de rapport** volet, faites glisser le `Date` champ la **groupes de lignes** volet. Placez-le au-dessus de la ligne appelée **(Details)**.  
  
     Notez que le descripteur de ligne comporte maintenant un crochet, qui indique un groupe. En outre, le tableau présente désormais deux colonnes Date, placées de part et d'autre d'une ligne verticale en pointillé.  
  
     ![](../../2014/tutorials/media/rs-basictablegroups1design.gif "rs_BasicTableGroups1Design")  
  
4.  À partir de la **les données de rapport** volet, faites glisser le `Order` champ la **groupes de lignes** volet. Placez-le au-dessous du champ Date et au-dessus de la ligne **(Details)**.  
  
     Notez que le descripteur de ligne comporte maintenant deux crochets, qui indiquent deux groupes. Le tableau présente désormais deux `Order` colonnes, trop.  
  
5.  Supprimer les colonnes de Date et l’ordre d’origine à la **droit** du double trait. Cette opération supprime les différentes valeurs d'enregistrement afin que seule la valeur de groupe soit affichée. Sélectionnez les descripteurs des deux colonnes, cliquez avec le bouton droit, puis cliquez sur **Supprimer les colonnes**.  
  
     ![Sélectionnez les colonnes à supprimer](../../2014/tutorials/media/rs-basictablegroupsdeletecols.gif "Sélectionnez les colonnes à supprimer")  
  
     Vous pouvez de nouveau mettre en forme la date et les en-têtes de colonne.  
  
6.  Sélectionnez l'onglet **Aperçu** pour afficher un aperçu du rapport. Il doit présenter un aspect similaire à l'illustration suivante :  
  
     ![Table regroupée par date, puis par commande](../../2014/tutorials/media/rs-basictablegroupspreview.gif "Table regroupée par date, puis par commande")  
  
##  <a name="bkmk_addtotals"></a> Pour ajouter des totaux à un rapport  
  
1.  Basculez en mode Conception.  
  
2.  Cliquez avec le bouton droit dans la cellule de région de données qui contient le champ `[LineTotal]`, puis sélectionnez **Ajouter un total**.  
  
     Cette opération ajoute une ligne avec la somme des montants en dollars de chaque commande.  
  
3.  Cliquez avec le bouton droit dans la cellule qui contient le champ `[Qty]`, puis cliquez sur **Ajouter un total**.  
  
     Cette opération ajoute la somme des quantités de chaque commande à la ligne des totaux.  
  
4.  Dans la cellule vide à gauche de `Sum[Qty]`, tapez l'étiquette «**Total des commandes**».  
  
5.  Vous pouvez ajouter une couleur d'arrière-plan à la ligne des totaux. Sélectionnez les deux cellules de somme et la cellule d'étiquette.  
  
6.  Dans le menu **Format** , cliquez sur **Couleur d'arrière-plan**, sur **Gris clair**, puis sur **OK**.  
  
     ![Mode Conception : Tableau de base avec total des commandes](../../2014/tutorials/media/rs-basictablesumlinetotaldesign.gif "mode conception : Tableau de base avec total des commandes")  
  
##  <a name="bkmk_adddailytotal"></a> Pour ajouter un total quotidien à un rapport  
  
1.  Avec le bouton droit de la cellule Order, pointez sur **ajouter un Total**, puis cliquez sur **après**.  
  
     Cette opération ajoute une nouvelle ligne contenant la somme des quantités et en dollars pour chaque jour et l’étiquette «**Total**» dans la colonne Order.  
  
2.  Tapez le mot **quotidien** après le mot **Total** dans la même cellule. Vous obtenez : **Total quotidien**.  
  
3.  Sélectionnez la cellule **Total quotidien** , les deux cellules de **somme** et la cellule vide qui les sépare.  
  
4.  Dans le menu **Format** , cliquez sur **Couleur d'arrière-plan**, sur **Orange**, puis sur **OK**.  
  
     ![](../../2014/tutorials/media/rs-basictablesumdaytotaldesign.gif "rs_BasicTableSumDayTotalDesign")  
  
##  <a name="bkmk_addgrandtotal"></a> Pour ajouter un total général à un rapport  
  
1.  Cliquez avec le bouton droit dans la cellule Date, pointez sur **Ajouter un total**, puis cliquez sur **Après**.  
  
     Cette opération ajoute une nouvelle ligne contenant la somme de la quantité de quantité et en dollars pour l’intégralité du rapport et le **Total** étiquette dans le `Date` colonne.  
  
2.  Tapez le mot **général** après le mot **Total** dans la même cellule. Vous obtenez : **Total général**.  
  
3.  Sélectionnez la cellule **Total général** , les deux cellules de **somme** et les cellules vides qui les séparent.  
  
4.  Dans le menu **Format** , cliquez sur **Couleur d'arrière-plan**, sur **Bleu clair**, puis sur **OK**.  
  
     ![Mode Conception : Total général dans la table de base](../../2014/tutorials/media/rs-basictablesumgrandtotaldesign.gif "mode conception : Total général dans la table de base")  
  
5.  Cliquez sur Aperçu.  
  
     La dernière page doit avoir l'aspect suivant :  
  
     ![Aperçu : Table de base avec total général](../../2014/tutorials/media/rs-basictablesumgrandtotalpreview.gif "Preview : Table de base avec total général")  
  
##  <a name="bkmk_publishreport"></a> Pour publier le rapport sur le serveur de rapports (facultatif)  
  
1.  Une étape facultative consiste à publier le rapport terminé sur le serveur de rapports en mode natif afin de pouvoir consulter le rapport à partir du Gestionnaire de rapports.  
  
2.  Dans la barre d'outils, cliquez sur **Projet** , puis sur **Propriétés du didacticiel...**  
  
3.  Dans le **TargetServerURL** tapez le nom du nom de votre serveur de rapports, par exemple **http://\<servername > / reportserver**  
  
4.  Cliquez sur **OK**  
  
5.  Dans la barre d'outils, cliquez sur **Générer** , puis sur **Déployer le didacticiel**.  
  
     Si vous voyez un message semblable à ce qui suit dans la fenêtre de sortie, c'est que le déploiement a été réalisé avec succès.  
  
    > ------ Création démarrée : Projet : tutorial, Configuration : débogage ------« Sales Orders.rdl » ignoré. L'élément est à jour.Fin de la génération -- 0 erreur, 0 avertissement------ Début du déploiement : Projet : tutorial, Configuration : Débogage---déploiement vers http://\<nom du serveur > / /reportserverdeploying report '/ tutorial/Sales Orders'. Fin du déploiement--0 erreur, 0 avertissement === générer : 1 réussi ou mis à jour, 0 échoué, 0 ignoré ==================== Déployer : 1 réussi, 0 échoué, 0 ignoré ==========  
  
     Si un message d'erreur semblable au suivant s'affiche, vérifiez que vous disposez d'autorisations sur le serveur de rapports et que vous avez démarré [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] avec des privilèges d'administrateur.  
  
    > « Les autorisations accordées à l’utilisateur « XXXXXXXX\\< votre nom d’utilisateur\>' sont insuffisantes pour effectuer cette opération »  
  
6.  Démarrez le Gestionnaire de rapports avec des privilèges d'administrateur ; cliquez, par exemple, avec le bouton droit sur l'icône d'Internet Explorer et sélectionnez **Exécuter en tant qu'administrateur**.  
  
     Accédez à l'URL du Gestionnaire de rapports, par exemple : `http://<server name>/reports`.  
  
7.  Accédez au dossier qui contient le rapport et cliquez sur le nom du rapport `Sales Orders` afin de consulter le rapport rendu dans le navigateur.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez réalisé le didacticiel de création d'un rapport de tableau de base.  
  
## <a name="see-also"></a>Voir aussi  
 [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
