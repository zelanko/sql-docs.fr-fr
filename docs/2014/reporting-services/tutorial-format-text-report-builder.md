---
title: 'Didacticiel : mettre en forme du texte (Générateur de rapports) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 67d8513e-8a70-464b-b87f-e91d010cfd82
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dc58232ed3025063fb329392b58895ed667465f4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66098903"
---
# <a name="tutorial-format-text-report-builder"></a>Didacticiel : mettre en forme du texte (Générateur de rapports)
  Dans ce didacticiel, vous pouvez vous entraîner à mettre en forme le texte de plusieurs façons. Après avoir configuré le rapport vierge avec la source de données et le dataset, vous pourrez choisir les étapes que vous souhaitez explorer.  
  
 L'illustration suivante montre un rapport similaire à celui que vous allez créer.  
  
 ![rs_FormatTextFinal](../../2014/tutorials/media/rs-formattextfinal.gif "rs_FormatTextFinal")  
  
 Dans une étape, vous allez sciemment générer une erreur afin de voir pourquoi il s'agit d'une erreur. Vous corrigerez ensuite l'erreur pour obtenir l'effet souhaité.  
  
 Une version améliorée du rapport créé dans ce didacticiel est disponible sous forme d'exemple de rapport Générateur de rapports de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Pour plus d’informations sur le téléchargement de cet exemple de rapport et d’autres, consultez [Générateur de rapports exemples de rapports](https://go.microsoft.com/fwlink/?LinkId=184851).  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a>Ce que vous allez apprendre  
  
### <a name="set-up-the-report"></a>Configurer le rapport  
 1. [Créer un rapport vierge avec une source de données et un DataSet](#CreateReport)  
  
 2. [Ajouter un champ à l'aire de conception du rapport (de façon incorrecte, puis correcte)](#AddField)  
  
 3. [Ajoutez une table au rapport Aire de conception](#AddTable)  
  
### <a name="pick-and-choose"></a>Choisir  
 [Ajouter un lien hypertexte au rapport](#AddHyperlink)  
  
 [Faire pivoter le texte dans le rapport](#RotateText)  
  
 [Affichage de texte avec une mise en forme HTML](#FormatHTML)  
  
 [Mettre en forme la devise](#FormatCurrency)  
  
 [Enregistrer le rapport](#Save)  
  
 Durée estimée pour effectuer le didacticiel : 20 minutes.  
  
## <a name="requirements"></a>Conditions requises  
 Pour plus d’informations sur les spécifications, consultez [Éléments requis pour les didacticiels &#40;Générateur de rapports&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="create-a-blank-report-with-a-data-source-and-dataset"></a><a name="CreateReport"></a>Créer un rapport vierge avec une source de données et un DataSet  
  
#### <a name="to-create-a-blank-report"></a>Pour créer un rapport vierge  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]sur **Générateur de rapports**, puis cliquez sur **Générateur de rapports**.  
  
    > [!NOTE]  
    >  La boîte de dialogue **Mise en route** s'affiche. Si elle ne s'affiche pas, à partir du bouton Générateur de rapports, cliquez sur **Nouveau**.  
  
2.  Dans le volet gauche de la boîte de dialogue **Mise en route** , assurez-vous que **Nouveau rapport** est sélectionné.  
  
3.  Dans le volet droit, cliquez sur **Rapport vierge**.  
  
#### <a name="to-create-a-data-source"></a>Pour créer une source de données  
  
1.  Dans le volet données du rapport, cliquez sur **nouveau**, puis sur **source de données**.  
  
2.  Dans la zone **Nom** , tapez **TextDataSource**  
  
3.  Cliquez sur **Utiliser une connexion incorporée dans mon rapport**.  
  
4.  Vérifiez que le type de connexion est Microsoft SQL Server, puis, dans la zone **Chaîne de connexion**, tapez **Data Source = \<nom_serveur>**  
  
    > [!NOTE]  
    >  L’expression \<ServerName>, par exemple rapport001, spécifie un ordinateur sur lequel une instance du SQL Server moteur de base de données est installée. Ce didacticiel n'a pas besoin de données spécifiques. Il a juste besoin d'une connexion à une base de données [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] . Si une connexion à une source de données est déjà répertoriée sous **Connexions à la source de données**, vous pouvez la sélectionner et passer à la procédure suivante, « Pour créer un dataset ». Pour plus d’informations, consultez [Autres manières d’obtenir une connexion de données &#40;Générateur de rapports&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-create-a-dataset"></a>Pour créer un dataset  
  
1.  Dans le volet des données de rapport, cliquez sur **Nouveau**, puis sur **Dataset**.  
  
2.  Vérifiez que la source de données est **TextDataSource**.  
  
3.  Dans la zone **Nom** , tapez **TextDataset**.  
  
4.  Vérifiez que le type de requête **Texte** est sélectionné, puis cliquez sur **Concepteur de requêtes**.  
  
5.  Cliquez sur **Modifier en tant que texte**.  
  
6.  Collez la requête suivante dans le volet de requête :  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    ```  
  
7.  Cliquez sur Exécuter (**!**) pour exécuter la requête.  
  
     Les résultats de la requête sont les données qui peuvent être affichées dans votre rapport.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="add-a-field-to-the-report-design-surface"></a><a name="AddField"></a>Ajoutez un champ au rapport Aire de conception  
 Si vous souhaitez qu'un champ de votre dataset apparaisse dans un rapport, votre premier réflexe peut être de le faire glisser directement sur l'aire de conception. Cet exercice montre pourquoi cela ne fonctionne pas et ce que vous devez faire à la place.  
  
#### <a name="to-add-a-field-to-the-report-and-get-the-wrong-result"></a>Pour ajouter un champ au rapport (et obtenir le résultat incorrect)  
  
1.  Faites glisser le champ **FullName** du volet Données du rapport vers l’aire de conception.  
  
     Générateur de rapports crée une zone de texte contenant une expression, représentée sous la \<forme expr>.  
  
2.  Cliquez sur **Exécuter**.  
  
     Notez qu’il n’existe qu’un seul enregistrement, **Fernando Ross**, qui est le premier enregistrement dans la requête par ordre alphabétique. Le champ ne se répète pas pour afficher les autres enregistrements.  
  
3.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
4.  Sélectionnez l’expression \<expr> dans la zone de texte.  
  
5.  Dans le volet Propriétés, les éléments suivants sont affichés pour la propriété **Valeur** (si le volet Propriétés n’est pas affiché, sous l’onglet **Affichage** , cochez **Propriétés**) :  
  
    ```  
    =First(Fields!FullName.Value, "TextDataSet")  
    ```  
  
     La fonction `First` permet de récupérer uniquement la première valeur d'un champ, et c'est ce qu'elle a fait.  
  
     Le fait de faire glisser le champ directement sur l'aire de conception a créé une zone de texte. Les zones de texte par elles-mêmes ne sont pas des régions de données et n'affichent donc pas les données d'un dataset de rapport. Les zones de texte dans les régions de données, comme les tableaux, les matrices et les listes, affichent des données.  
  
6.  Sélectionnez la zone de texte (si l'expression est sélectionnée, appuyez sur Échap pour sélectionner la zone de texte) et appuyez sur la touche Suppr.  
  
#### <a name="to-add-a-field-to-the-report-and-get-the-right-result"></a>Pour ajouter un champ au rapport (et obtenir le résultat correct)  
  
1.  Sous l’onglet **Insertion** du Ruban, dans la zone **Régions de données** , cliquez sur **Liste**. Cliquez sur l'aire de conception, puis faites glisser la souris pour créer une zone d'environ 5 cm de large sur 2,5 cm de haut.  
  
2.  Faites glisser le champ **FullName** du volet Données du rapport vers la zone de liste.  
  
     Cette fois, le Générateur de rapports crée une zone de texte contenant l’expression `[FullName]` .  
  
3.  Cliquez sur **Exécuter**.  
  
     Notez que cette fois, la zone se répète de manière à afficher tous les enregistrements de la requête.  
  
4.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
5.  Sélectionnez l'expression dans la zone de texte.  
  
6.  Dans le volet Propriétés, les éléments suivants sont affichés pour la propriété **Valeur** :  
  
    ```  
    =Fields!FullName.Value  
    ```  
  
     En faisant glisser la zone de texte vers la région de données de liste, vous affichez les données du dataset.  
  
7.  Sélectionnez la zone de liste et appuyez sur la touche Suppr.  
  
##  <a name="add-a-table-to-the-report-design-surface"></a><a name="AddTable"></a>Ajoutez une table au rapport Aire de conception  
 Créez cette table pour avoir un emplacement où placer les liens hypertexte et le texte pivoté.  
  
#### <a name="to-add-a-table-to-the-report"></a>Pour ajouter un tableau au rapport  
  
1.  Dans le menu **Insérer** , cliquez sur **tableau**, puis sur **Assistant Tableau**.  
  
2.  Dans la page **choisir un DataSet** de l’Assistant Nouveau tableau ou nouvelle matrice, cliquez sur **choisir un DataSet existant dans ce rapport ou un dataset partagé**, puis cliquez sur **TextDataset (dans ce rapport)**, puis cliquez sur **suivant**.  
  
3.  Dans la **page organiser les champs** , faites glisser les champs **secteur**, **linktext**et **produit** vers **groupes de lignes**, faites glisser le champ **Sales** vers **valeurs**, puis cliquez sur **suivant**.  
  
4.  Dans la page **choisir la disposition** , désactivez la case à cocher **développer/réduire les groupes** afin de pouvoir voir le tableau entier, puis cliquez sur **suivant**.  
  
5.  Dans la page **choisir un style** , cliquez sur **ardoise**, puis sur **Terminer**.  
  
6.  Faites glisser le tableau sous le bloc de titre.  
  
7.  Cliquez sur **Exécuter**.  
  
     Le tableau semble parfait, mais il contient deux lignes de total. Le champ **linktext** n’a pas besoin d’une ligne de total.  
  
8.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
9. Cliquez avec le bouton droit sur la zone `[LinkText]`de texte qui contient, puis cliquez sur **fractionner les cellules**.  
  
10. Sélectionnez la cellule vide sous la `[LinkText]` cellule, maintenez la touche Maj enfoncée et sélectionnez les deux cellules à droite : la cellule **total** dans la colonne **Product** et la `[Sum(Sales)]` cellule dans la colonne **Sales** .  
  
11. Après avoir sélectionné ces trois cellules, cliquez avec le bouton droit sur l’une de ces cellules, puis cliquez sur **Supprimer la ligne**.  
  
12. Cliquez sur **Exécuter**.  
  
##  <a name="add-a-hyperlink-to-the-report"></a><a name="AddHyperlink"></a>Ajouter un lien hypertexte au rapport  
 Dans cette section, vous allez ajouter un lien hypertexte au texte du tableau de la section précédente.  
  
#### <a name="to-add-a-hyperlink-to-the-report"></a>Pour ajouter un lien hypertexte au rapport  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Cliquez avec le bouton droit dans la cellule qui contient `[LinkText]`, puis cliquez sur **Propriétés de la zone de texte**.  
  
3.  Dans la zone Propriétés de la **zone de texte** , cliquez sur **action**.  
  
4.  Cliquez sur **accéder à l’URL**.  
  
5.  Dans la zone **Sélectionner une URL** , cliquez sur **[URL]**, puis sur **OK**.  
  
6.  Notez que le texte n'est en aucune manière différent. Vous devez lui donner l'apparence de texte de lien.  
  
7.  Sélectionnez `[LinkText]`.  
  
8.  Dans la section **police** de l’onglet dossier de **démarrage** , cliquez sur le bouton **souligné** , puis cliquez sur la flèche déroulante en regard du bouton **couleur** , puis cliquez sur **bleu**.  
  
9. Cliquez sur **Exécuter**.  
  
     Le texte a maintenant l'apparence d'un lien.  
  
10. Cliquez sur un lien. Si l'ordinateur est connecté à Internet, un navigateur s'ouvre sur une rubrique d'aide du Générateur de rapports.  
  
##  <a name="rotate-text-in-the-report"></a><a name="RotateText"></a>Faire pivoter le texte dans le rapport  
 Dans cette section, vous allez faire pivoter une partie du texte du tableau des sections précédentes.  
  
#### <a name="to-rotate-text"></a>Pour faire pivoter le texte  
  
1.  Cliquez sur **Conception** pour repasser en mode Conception.  
  
2.  Cliquez dans la cellule qui contient `[Territory].`  
  
3.  Sous l’onglet **Accueil** , dans la section **Police** , cliquez sur le bouton **Gras** .  
  
4.  Si le volet Propriétés n’est pas ouvert, sous l’onglet **Affichage** , cochez la case **Propriétés** .  
  
5.  Recherchez la propriété WritingMode dans le volet Propriétés.  
  
    > [!NOTE]  
    >  Quand les propriétés du volet Propriétés sont organisées en catégories, WritingMode figure dans la catégorie **Localisation** . Assurez-vous que vous avez sélectionné la cellule et non le texte. WritingMode est une propriété de la zone de texte, pas du texte.  
  
6.  Dans la zone de liste, cliquez sur **Rotate270**.  
  
7.  Dans l’onglet dossier de **démarrage** de la section **paragraphe** , cliquez sur les boutons **centraux** et **centraux** pour localiser le texte au centre de la cellule à la fois verticalement et horizontalement.  
  
8.  Cliquez sur Exécuter (**!**).  
  
 Le texte de la cellule `[Territory]` s'exécute maintenant verticalement de bas en haut des cellules.  
  
##  <a name="displaying-text-with-html-formatting"></a><a name="FormatHTML"></a>Affichage de texte avec une mise en forme HTML  
  
#### <a name="to-display-text-formatted-as-html"></a>Pour afficher le texte mis en forme en HTML  
  
1.  Cliquez sur **Conception** pour basculer en mode Conception.  
  
2.  Sous l’onglet **Insertion** , cliquez sur **Zone de texte**, puis sur l’aire de conception, cliquez et faites glisser la souris pour créer une zone de texte sous le tableau d’environ 10 cm de large sur 8 cm de haut.  
  
3.  Copiez le texte suivant et collez-le dans la zone de texte :  
  
    ```  
    <h4>Limitations of cascading style sheet attributes</h4>  
          <p>Only a basic set of <b>cascading style sheet (CSS)</b> attributes are defined:</p>  
          <ul><li>  
              text-align, text-indent  
            </li><li>  
              font-family, font-size  
            </li><li>  
              color  
            </li><li>  
              padding, padding-bottom, padding-top, padding-right, padding-left  
            </li><li>  
              font-weight  
            </li></ul>  
    ```  
  
4.  Sélectionnez tout le texte de la zone de texte.  
  
     Il s'agit d'une propriété du texte, pas de la zone de texte. Ainsi, une zone de texte peut contenir à la fois du texte brut et du texte qui utilise des balises HTML comme styles.  
  
5.  Cliquez avec le bouton droit sur l’ensemble du texte sélectionné, puis cliquez sur **Propriétés du texte**.  
  
6.  Sur la page **général** , sous **type de balise**, cliquez sur **HTML-interpréter les balises html comme des styles**.  
  
7.  Cliquez sur **OK**.  
  
8.  Cliquez sur Exécuter (**!**) pour afficher un aperçu du rapport.  
  
 Le texte de la zone de texte est affiché sous forme de titre, paragraphe et liste à puce.  
  
##  <a name="format-currency"></a><a name="FormatCurrency"></a>Mettre en forme la devise  
  
#### <a name="to-format-numbers-as-currency"></a>Pour mettre en forme des nombres en devise  
  
1.  Cliquez sur **Conception** pour basculer en mode Conception.  
  
2.  Cliquez sur la cellule supérieure du tableau contenant `[Sum(Sales)]`, maintenez la touche Maj enfoncée et cliquez sur la cellule inférieure du tableau contenant `[Sum(Sales)]`.  
  
3.  Sous l’onglet **Accueil** , dans le groupe **Nombre** , cliquez sur le bouton **Devise** .  
  
4.  Facultatif Dans l’onglet dossier de **démarrage** , dans le groupe **nombre** , cliquez sur le bouton **styles des espaces réservés** et cliquez sur **exemples de valeurs** pour voir comment les nombres sont mis en forme.  
  
5.  (Facultatif) Sous l’onglet **Accueil** , dans le groupe **Nombre** , cliquez sur le bouton **Réduire les décimales** à deux reprises, pour afficher les valeurs en dollars sans indication de centimes.  
  
6.  Cliquez sur Exécuter (**!**) pour afficher un aperçu du rapport.  
  
 Le rapport affiche maintenant les données mises en forme et est plus facile à lire.  
  
##  <a name="save-the-report"></a><a name="Save"></a>Enregistrer le rapport  
 Vous pouvez enregistrer les rapports sur un serveur de rapports, dans une bibliothèque SharePoint ou sur l'ordinateur.  
  
 Dans ce didacticiel, enregistrez le rapport sur un serveur de rapports. Si vous n'avez pas accès à un serveur de rapports, enregistrez le rapport sur votre ordinateur.  
  
#### <a name="to-save-the-report-on-a-report-server"></a>Pour enregistrer le rapport sur un serveur de rapports  
  
1.  À partir du bouton **Générateur de rapports** , cliquez sur **Enregistrer sous**.  
  
2.  Cliquez sur **Sites et serveurs récents**.  
  
3.  Sélectionnez ou tapez le nom du serveur de rapports sur lequel vous êtes autorisé à enregistrer des rapports.  
  
     Le message « Connexion au serveur de rapports » s'affiche. Une fois la connexion établie, le contenu du dossier de rapports spécifié par l'administrateur du serveur de rapports s'affiche comme emplacement par défaut des rapports.  
  
4.  Dans **Nom**, remplacez le nom par défaut par un nom de votre choix.  
  
5.  Cliquez sur **Save**.  
  
 Le rapport est enregistré sur le serveur de rapports. Le nom du serveur de rapports auquel vous êtes connecté est indiqué dans la barre d'état située au bas de la fenêtre.  
  
#### <a name="to-save-the-report-on-your-computer"></a>Pour enregistrer le rapport sur votre ordinateur  
  
1.  À partir du bouton **Générateur de rapports** , cliquez sur **Enregistrer sous**.  
  
2.  Cliquez sur **Bureau**, **Mes documents**ou **Poste de travail**, puis naviguez jusqu'au dossier où vous souhaitez enregistrer le rapport.  
  
3.  Dans **Nom**, remplacez le nom par défaut par un nom de votre choix.  
  
4.  Cliquez sur **Save**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Il existe de nombreuses façons de mettre en forme du texte dans Générateur de rapports [Didacticiel : la création d’un rapport de forme libre &#40;Générateur de rapports&#41;](../reporting-services/tutorial-creating-a-free-form-report-report-builder.md) contient plus d’exemples.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels &#40;Générateur de rapports&#41;](report-builder-tutorials.md)   
 [Mise en forme des éléments de rapport &#40;Générateur de rapports et SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md)   
 [Générateur de rapports dans SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
