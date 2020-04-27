---
title: 'Leçon 6 : Ajouter un regroupement et des totaux (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e3d61228-2aa4-42cc-955e-602dbf3406a7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5607dfb046e7f50eb3a015e1f4f13711256435a8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108413"
---
# <a name="lesson-6-adding-grouping-and-totals-reporting-services"></a>Leçon 6 : Ajout d'un regroupement et de totaux (Reporting Services)
  Ajoutez un regroupement et des totaux à votre rapport pour organiser et synthétiser vos données.  
  
 Pour plus d’informations sur l’ajout de totaux cumulés à des rapports, voir : [Ajout de totaux à des rapports Reporting Services (SSRS)](https://www.tutorialgateway.org/add-total-and-subtotal-to-ssrs-report/).  
  
 **Dans cette rubrique :**  
  
-   [Pour regrouper des données dans un rapport](#bkmk_groupdata)  
  
-   [Pour ajouter des totaux à un rapport](#bkmk_addtotals)  
  
-   [Pour ajouter un total quotidien à un rapport](#bkmk_adddailytotal)  
  
-   [Pour ajouter un total général à un rapport](#bkmk_addgrandtotal)  
  
-   [Pour publier le rapport sur le serveur de rapports (facultatif)](#bkmk_publishreport)  
  
##  <a name="to-group-data-in-a-report"></a><a name="bkmk_groupdata"></a>Pour regrouper des données dans un rapport  
  
1.  Cliquez sur l'onglet **Conception** .  
  
2.  Si vous ne voyez pas le volet **Groupes de lignes** , cliquez avec le bouton droit sur l'aire de conception, puis sélectionnez **Vue** et cliquez sur **Regroupement**.  
  
3.  Faites glisser le champ `Date` du volet **Données du rapport** vers le volet **Groupes de lignes**. Placez-le au-dessus de la ligne appelée **(Details)**.  
  
     Notez que le descripteur de ligne comporte maintenant un crochet, qui indique un groupe. En outre, le tableau présente désormais deux colonnes Date, placées de part et d'autre d'une ligne verticale en pointillé.  
  
     ![](../../2014/tutorials/media/rs-basictablegroups1design.gif "rs_BasicTableGroups1Design")  
  
4.  Faites glisser le champ `Order` du volet **Données du rapport** vers le volet **Groupes de lignes**. Placez-le au-dessous du champ Date et au-dessus de la ligne **(Details)**.  
  
     Notez que le descripteur de ligne comporte maintenant deux crochets, qui indiquent deux groupes. La table comporte désormais deux `Order` colonnes.  
  
5.  Supprimez les colonnes Date et Order d’origine, à **droite** du double trait. Cette opération supprime les différentes valeurs d'enregistrement afin que seule la valeur de groupe soit affichée. Sélectionnez les descripteurs des deux colonnes, cliquez avec le bouton droit, puis cliquez sur **Supprimer les colonnes**.  
  
     ![Sélectionner les colonnes à supprimer](../../2014/tutorials/media/rs-basictablegroupsdeletecols.gif "Sélectionner les colonnes à supprimer")  
  
     Vous pouvez de nouveau mettre en forme la date et les en-têtes de colonne.  
  
6.  Sélectionnez l'onglet **Aperçu** pour afficher un aperçu du rapport. Il doit présenter un aspect similaire à l'illustration suivante :  
  
     ![Table regroupée par date, puis par commande](../../2014/tutorials/media/rs-basictablegroupspreview.gif "Table regroupée par date, puis par commande")  
  
##  <a name="to-add-totals-to-a-report"></a><a name="bkmk_addtotals"></a>Pour ajouter des totaux à un rapport  
  
1.  Basculez en mode Conception.  
  
2.  Cliquez avec le bouton droit dans la cellule de région de données qui contient le champ `[LineTotal]`, puis sélectionnez **Ajouter un total**.  
  
     Cette opération ajoute une ligne avec la somme des montants en dollars de chaque commande.  
  
3.  Cliquez avec le bouton droit dans la cellule qui contient le champ `[Qty]`, puis cliquez sur **Ajouter un total**.  
  
     Cette opération ajoute la somme des quantités de chaque commande à la ligne des totaux.  
  
4.  Dans la cellule vide à gauche de `Sum[Qty]`, tapez l'étiquette «**Total des commandes**».  
  
5.  Vous pouvez ajouter une couleur d'arrière-plan à la ligne des totaux. Sélectionnez les deux cellules de somme et la cellule d'étiquette.  
  
6.  Dans le menu **Format** , cliquez sur **Couleur d'arrière-plan**, sur **Gris clair**, puis sur **OK**.  
  
     ![Mode Conception : table de base avec total des commandes](../../2014/tutorials/media/rs-basictablesumlinetotaldesign.gif "Mode Conception : table de base avec total des commandes")  
  
##  <a name="to-add-a-daily-total-to-a-report"></a><a name="bkmk_adddailytotal"></a>Pour ajouter un total quotidien à un rapport  
  
1.  Cliquez avec le bouton droit dans la cellule Order , pointez sur **Ajouter un total**, puis cliquez sur **Après**.  
  
     Cela ajoute une nouvelle ligne contenant les sommes des quantités et des montants en dollars pour chaque jour, et l’étiquette «**total**» dans la colonne Order.  
  
2.  Tapez le mot **quotidien** après le mot **Total** dans la même cellule. Vous obtenez : **Total quotidien**.  
  
3.  Sélectionnez la cellule **Total quotidien** , les deux cellules de **somme** et la cellule vide qui les sépare.  
  
4.  Dans le menu **Format** , cliquez sur **Couleur d'arrière-plan**, sur **Orange**, puis sur **OK**.  
  
     ![](../../2014/tutorials/media/rs-basictablesumdaytotaldesign.gif "rs_BasicTableSumDayTotalDesign")  
  
##  <a name="to-add-a-grand-total-to-a-report"></a><a name="bkmk_addgrandtotal"></a>Pour ajouter un total général à un rapport  
  
1.  Cliquez avec le bouton droit dans la cellule Date, pointez sur **Ajouter un total**, puis cliquez sur **Après**.  
  
     Cette opération ajoute une nouvelle ligne contenant la somme des quantités et des montants en dollars pour l’intégralité du **Total** rapport, ainsi que `Date` l’étiquette totale de la colonne.  
  
2.  Tapez le mot **général** après le mot **Total** dans la même cellule. Vous obtenez : **Total général**.  
  
3.  Sélectionnez la cellule **Total général** , les deux cellules de **somme** et les cellules vides qui les séparent.  
  
4.  Dans le menu **Format** , cliquez sur **Couleur d'arrière-plan**, sur **Bleu clair**, puis sur **OK**.  
  
     ![Mode Conception : total général dans table de base](../../2014/tutorials/media/rs-basictablesumgrandtotaldesign.gif "Mode Conception : total général dans table de base")  
  
5.  Cliquez sur Aperçu.  
  
     La dernière page doit avoir l'aspect suivant :  
  
     ![Aperçu : table de base avec total général](../../2014/tutorials/media/rs-basictablesumgrandtotalpreview.gif "Aperçu : table de base avec total général")  
  
##  <a name="to-publish-the-report-to-the-report-server-optional"></a><a name="bkmk_publishreport"></a>Pour publier le rapport sur le serveur de rapports (facultatif)  
  
1.  Une étape facultative consiste à publier le rapport terminé sur le serveur de rapports en mode natif afin de pouvoir consulter le rapport à partir du Gestionnaire de rapports.  
  
2.  Dans la barre d'outils, cliquez sur **Projet** , puis sur **Propriétés du didacticiel...**  
  
3.  Dans **TargetServerURL** , tapez le nom du serveur de rapports, par exemple **http://\<ServerName>/ReportServer** .  
  
4.  Cliquez sur **OK**  
  
5.  Dans la barre d'outils, cliquez sur **Générer** , puis sur **Déployer le didacticiel**.  
  
     Si vous voyez un message semblable à ce qui suit dans la fenêtre de sortie, c'est que le déploiement a été réalisé avec succès.  
  
    > ------ Création démarrée : Projet : didacticiel, Configuration : débogage ------« Sales Orders.rdl » ignoré. L’élément est à jour. Fin de la génération--0 erreur, 0 avertissement------le déploiement a démarré : projet : didacticiel, configuration : déboguer------déployant sur le nom du serveur http://\<>/reportserverdeploying rapport « /Tutorial/Sales Orders ». Fin du déploiement--0 erreur, 0 AVERTISSEMENT = = = = = = = = = = Build : 1 a réussi ou à jour, 0 a échoué, 0 a été ignoré = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = = =  
  
     Si un message d'erreur semblable au suivant s'affiche, vérifiez que vous disposez d'autorisations sur le serveur de rapports et que vous avez démarré [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] avec des privilèges d'administrateur.  
  
    > « Les autorisations accordées à l’utilisateur\\ «xxxxxxxx<votre\>nom d’utilisateur » ne sont pas suffisantes pour effectuer cette opération»  
  
6.  Démarrez le Gestionnaire de rapports avec des privilèges d'administrateur ; cliquez, par exemple, avec le bouton droit sur l'icône d'Internet Explorer et sélectionnez **Exécuter en tant qu'administrateur**.  
  
     Accédez à l'URL du Gestionnaire de rapports, par exemple : `http://<server name>/reports`.  
  
7.  Accédez au dossier qui contient le rapport et cliquez sur le nom du rapport `Sales Orders` afin de consulter le rapport rendu dans le navigateur.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez réalisé le didacticiel de création d'un rapport de tableau de base.  
  
## <a name="see-also"></a>Voir aussi  
 [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
