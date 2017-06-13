---
title: "Didacticiel : Créer un rapport de graphique rapide en mode hors connexion (Générateur de rapports) | Documents Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reports, creating
- tutorials, getting started
- creating reports
ms.assetid: 6b1db67a-cf75-494c-b70c-09f1e6a8d414
caps.latest.revision: 31
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: a09ebdeda6679c80f3eb32602d38068114e7bf36
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---

# <a name="tutorial-create-a-quick-chart-report-offline-report-builder"></a>Didacticiel : créer un rapport de graphique rapide en mode hors connexion (Générateur de rapports)

  Dans ce didacticiel, vous allez utiliser un assistant pour créer un graphique à secteurs dans un rapport paginé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)]. Vous ajoutez ensuite des pourcentages et modifiez légèrement le graphique à secteurs. 
  
Vous pouvez effectuer ce didacticiel de deux façons différentes. Les deux méthodes aboutissent au même résultat, à savoir un graphique à secteurs semblable à celui de cette illustration :  
  
 ![Graphique à secteurs rapide de générateur de rapports](../../reporting-services/report-builder/media/report-builder-quick-pie-chart.png "graphique à secteurs rapide de générateur de rapports")  
  
## <a name="prerequisites"></a>Conditions préalables  
 Si vous utilisez des données XML ou un [!INCLUDE[tsql](../../includes/tsql-md.md)] requête, vous devez avoir accès au Générateur de rapports. Vous pouvez démarrer le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] d’un serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif ou en mode intégré SharePoint, ou vous pouvez télécharger [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] à partir du Centre de téléchargement Microsoft. Pour plus d’informations, consultez [Install Report Builder](../../reporting-services/install-windows/install-report-builder.md).  
  
##  <a name="TwoWays"></a> Deux façons de réaliser ce didacticiel  
  
-   [Créer le graphique à secteurs avec des données XML](#CreatePieChartXML)  
  
-   [Créer le graphique à secteurs avec une requête Transact-SQL qui contient des données](#CreatePieQueryData)  
  
### <a name="using-xml-data-for-this-tutorial"></a>Utilisation de données XML pour ce didacticiel  
 Vous pouvez utiliser des données XML que vous copiez à partir de cette rubrique et que vous collez dans l'Assistant. Vous n’avez pas besoin d’être connecté à un [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] mode de serveur de rapports en mode natif ou SharePoint intégré, et vous n’avez pas besoin d’accéder à une instance de SQL Server.  
  
 [Créer le graphique à secteurs avec des données XML](#CreatePieChartXML)  
  
### <a name="using-a-includetsqlincludestsql-mdmd-query-that-contains-data-for-this-tutorial"></a>Utilisation d’une requête [!INCLUDE[tsql](../../includes/tsql-md.md)] qui contient les données de ce didacticiel  
 Vous pouvez copier une requête comprenant des données incluses à partir de cette rubrique et la coller dans l'Assistant. Vous avez besoin du nom d’une instance de SQL Server et les informations d’identification suffisant pour l’accès en lecture seule aux bases de données. La requête de dataset dans le didacticiel utilise des données littérales, mais la requête doit être traitée par une instance de SQL Server pour retourner les métadonnées qui est requises pour un dataset de rapport.  
  
 L’avantage lié à l’utilisation de la requête [!INCLUDE[tsql](../../includes/tsql-md.md)] vient du fait que tous les autres didacticiels du [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] utilisent la même méthode ; par conséquent, vous savez déjà quoi faire lorsque vous effectuez d’autres didacticiels.  
  
 La requête [!INCLUDE[tsql](../../includes/tsql-md.md)] requiert quelques conditions préalables supplémentaires. Pour plus d’informations, voir [Éléments requis pour les didacticiels (Générateur de rapports)](../../reporting-services/prerequisites-for-tutorials-report-builder.md).  
  
 [Créer le graphique à secteurs avec une requête Transact-SQL qui contient des données](#CreatePieQueryData)  
  
##  <a name="CreatePieChartXML"></a> Création du graphique à secteurs avec des données XML  
  
1.  [Démarrez le Générateur de rapport](../../reporting-services/report-builder/start-report-builder.md) à partir du portail web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , du serveur de rapports en mode intégré SharePoint, ou de votre ordinateur.  
  
     La boîte de dialogue **Mise en route** s'affiche.  
  
     ![Démarrer le Générateur de rapports](../../reporting-services/media/rb-getstarted.png "démarrer le Générateur de rapports")  
  
     If the **Getting Started** dialog box does not appear, click **File** >**New**. La boîte de dialogue **Nouveau rapport ou dataset** contient une grande partie des contenus de la boîte de dialogue **Mise en route** .  
  
2.  Dans le volet gauche, assurez-vous que **Nouveau rapport** est sélectionné.  
  
3.  Dans le volet droit, cliquez sur **Assistant Graphique**, puis sur **Créer**.  
  
4.  Dans la page **Choisir un dataset** , cliquez sur **Créer un dataset**, puis sur **Suivant**.  
  
5.  Dans la page **Choisir une connexion à une source de données** , cliquez sur **Nouveau**.  
  
     La boîte de dialogue **Propriétés de la source de données** s'ouvre.  
  
6.  Vous pouvez attribuer à la source de données le nom de votre choix. Dans la zone **Nom** , tapez **MonGraphiqueàSecteurs**.  
  
7.  Dans la zone **Sélectionner un type de connexion** , cliquez sur **XML**.  
  
8.  Cliquez sur l’onglet **Informations d’identification**, sélectionnez **Utiliser l’utilisateur Windows actuel. Une délégation Kerberos peut être nécessaire**, puis cliquez sur **OK**.  
  
9. Dans la page **Choisir une connexion à une source de données** , cliquez sur **MonGraphiqueàSecteurs**, puis sur **Suivant**.  
  
10. Copiez le texte suivant et collez-le dans la grande zone située en haut de la page **Créer une requête** .  
  
    ```  
    <Query>  
    <ElementPath>Root /S  {@Sales (Integer)} /C {@FullName} </ElementPath>  
    <XmlData>  
    <Root>  
    <S Sales="150">  
      <C FullName="Jae Pak" />  
    </S>  
    <S Sales="350">  
      <C FullName="Jillian  Carson" />  
    </S>  
    <S Sales="250">  
      <C FullName="Linda C Mitchell" />  
    </S>  
    <S Sales="500">  
      <C FullName="Michael Blythe" />  
    </S>  
    <S Sales="450">  
      <C FullName="Ranjit Varkey" />  
    </S>  
    </Root>  
    </XmlData>  
    </Query>  
    ```  
  
11. (Facultatif) Cliquez sur le **exécuter** bouton (**!**) pour afficher les données dépendra de votre graphique.  
  
     ![Concevoir une requête Générateur de rapports](../../reporting-services/report-builder/media/rb-designquery.png "concevoir une requête Générateur de rapports")  
  
12. Cliquez sur **Suivant**.  
  
13. Dans la page **Choisir un type de graphique** , cliquez sur **Secteurs**, puis sur **Suivant**.  
  
14. Dans le **organiser les champs du graphique** page, double-cliquez sur le **Sales** champ dans le **champs disponibles** boîte.  
  
     Notez que ce champ est déplacé automatiquement vers la zone **Valeurs** , car il s'agit d'une valeur numérique.  
  
     ![Assistant Générateur organiser les champs de rapport](../../reporting-services/report-builder/media/rb-wizarrangefields.png "Assistant Générateur de rapports organiser les champs")  
  
15. Faites glisser le **FullName** champ le **champs disponibles** boîte à la **catégories** boîte de (ou double-cliquez dessus ; il passera à la **catégories** boîte de), puis cliquez sur **suivant**.  
  
     La page d’aperçu montre le nouveau graphique à secteurs avec données représentationnelles. La légende indique Full Name 1, Full Name 2, etc., plutôt que les noms des agents commerciaux, et la taille des secteurs du graphique est incorrecte. Cela vous donne néanmoins une idée de l'aspect qu'aura votre rapport.  
  
     ![Rapport Générateur de nouveaux graphiques aperçu](../../reporting-services/report-builder/media/rb-newchartpreview.png "l’aperçu du graphique nouveau générateur de rapports")  
  
16. Cliquez sur **Terminer**.  
  
     Vous voyez à présent votre nouveau rapport de graphique à secteurs dans la vue Design, toujours avec des données représentationnelles.  
  
     ![À secteurs de nouveau générateur en mode Création de rapports](../../reporting-services/report-builder/media/rb-newpiedesign.png "à secteurs de nouveau générateur en mode Création de rapports")  
  
17. Pour afficher votre graphique à secteurs, cliquez sur **Exécuter** sous l'onglet **Accueil** du ruban.  
  
     ![Rapport Générateur de nouveaux graphiques exécuter](../../reporting-services/report-builder/media/rb-newchartrun.png "générateur nouveau plan d’exécution de rapports")  
  
18. Pour continuer à modifier votre graphique à secteurs, accédez à [Après l'exécution de l'Assistant](#AfterWizard) dans cet article.  
  
##  <a name="CreatePieQueryData"></a> Création du graphique à secteurs avec une requête [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
1.  [Démarrez le Générateur de rapport](../../reporting-services/report-builder/start-report-builder.md) à partir du portail web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , du serveur de rapports en mode intégré SharePoint, ou de votre ordinateur.  
  
     La boîte de dialogue **Mise en route** s'affiche.  
  
    > [!NOTE]  
    >  If the **Getting Started** dialog box does not appear, click **File** >**New**. La boîte de dialogue **Nouveau rapport ou dataset** contient une grande partie des contenus de la boîte de dialogue **Mise en route** .  
  
2.  Dans le volet gauche, assurez-vous que **Nouveau rapport** est sélectionné.  
  
3.  Dans le volet droit, cliquez sur **Assistant Graphique**, puis sur **Créer**.  
  
4.  Dans la page **Choisir un dataset** , cliquez sur **Créer un dataset**, puis sur **Suivant**.  
  
5.  Dans la page **Choisir une connexion à une source de données** , sélectionnez une source de données existante ou naviguez jusqu'au serveur de rapports, sélectionnez une source de données, puis cliquez sur **Suivant**. Vous devrez peut-être entrer un nom d'utilisateur et un mot de passe.  
  
    > [!NOTE]  
    >  La source de données que vous choisissez n'a pas d'importance, tant que vous disposez des autorisations appropriées. Vous n'allez pas récupérer de données à partir de la source de données. Pour plus d’informations, voir [Éléments requis pour les didacticiels (Générateur de rapports)](../../reporting-services/prerequisites-for-tutorials-report-builder.md).  
  
6.  Dans la page **Créer une requête** , cliquez sur **Modifier en tant que texte**.  
  
7.  Collez la requête suivante dans le volet de requête :  
  
    ```  
    SELECT 150 AS Sales, 'Jae Pak' AS FullName   
    UNION SELECT 350 AS Sales, 'Jillian Carson' AS FullName   
    UNION SELECT 250 AS Sales, 'Linda C Mitchell' AS FullName   
    UNION SELECT 500 AS Sales, 'Michael Blythe' AS FullName   
    UNION SELECT 450 AS Sales, 'Ranjit Varkey' AS FullName   
    ```  
  
8.  (Facultatif) Cliquez sur le bouton Exécuter (**!**) pour voir les données sur lesquelles votre graphique sera basé.  
  
9. Cliquez sur **Suivant**.  
  
10. Dans la page **Choisir un type de graphique** , cliquez sur **Secteurs**, puis sur **Suivant**.  
  
11. Dans le **organiser les champs du graphique** page, double-cliquez sur le **Sales** champ dans le **champs disponibles** boîte.  
  
     Notez que ce champ est déplacé automatiquement vers la zone **Valeurs** , car il s'agit d'une valeur numérique.  
  
12. Faites glisser le **FullName** champ le **champs disponibles** boîte à la **catégories** boîte de (ou double-cliquez dessus ; il passera à la **catégories** boîte de), puis cliquez sur **suivant**.  
  
13. Cliquez sur **Terminer**.  
  
     Votre nouveau graphique à secteurs est maintenant affiché sur l'aire de conception. Il ne s'agit que d'une représentation. La légende indique Full Name 1, Full Name 2, etc., plutôt que les noms des agents commerciaux, et la taille des secteurs du graphique est incorrecte. Cela vous donne néanmoins une idée de l'aspect qu'aura votre rapport.  
  
15. Pour afficher votre graphique à secteurs, cliquez sur **Exécuter** sous l'onglet **Accueil** du ruban.  
 
##  <a name="AfterWizard"></a> Après l'exécution de l'Assistant  
 Maintenant que vous avez créé votre rapport de graphique à secteurs, vous pouvez le manipuler. Sous l'onglet **Exécuter** du ruban, cliquez sur **Conception**de manière à pouvoir continuer de le modifier.  
  
## <a name="make-the-chart-bigger"></a>Augmenter la taille du graphique  
 Vous pouvez augmenter la taille du graphique à secteurs. 
 
*  Cliquez sur le graphique (mais pas sur l'un de ses éléments) pour le sélectionner et faites glisser le coin inférieur droit pour le redimensionner.  

Notez que l’aire de conception s’agrandit lorsque vous faites glisser.
  
## <a name="add-a-report-title"></a>Ajouter un titre de rapport  
1. Sélectionnez les mots **Titre du graphique** en haut du graphique, puis tapez un titre, par exemple : **Graphique à secteurs des ventes**.  
2. Avec le titre sélectionné, dans le volet Propriétés, modifiez **couleur** à **noir** et **FontSize** à **12pt**.
  
## <a name="add-percentages"></a>Ajouter des pourcentages  
 
1.  Cliquez sur le graphique à secteurs et sélectionnez **afficher les étiquettes de données**. Les étiquettes de données apparaissent dans chaque secteur du graphique.  
  
2.  Les étiquettes d’avec le bouton droit et sélectionnez **propriétés étiquette de la série**. La boîte de dialogue **Propriétés de l'étiquette de la série** s'affiche.  
  
3.  Dans le **étiqueter des données** , tapez **#PERCENT {P0}**.  
  
     **{P0}** indique le pourcentage sans décimales. Si vous tapez simplement **#PERCENT**, vos chiffres comporteront deux décimales. **#PERCENT** est un mot clé qui effectue un calcul ou une fonction pour vous ; il existe de nombreux autres.  
     
4. Cliquez sur **Oui** pour confirmer que vous voulez définir la valeur **UseValueAsLabel** sur **False**.

5. Sous l’onglet **Police** , sélectionnez **ras** , puis modifiez **Couleur** en **Blanc**.

6. Cliquez sur **OK**.     
  
 Pour plus d’informations sur la personnalisation des étiquettes et légendes de graphique, voir [Afficher des valeurs en pourcentage dans un graphique à secteurs (Générateur de rapports et SSRS)](../../reporting-services/report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md) et [Modifier le texte d’un élément de légende (Générateur de rapports et SSRS)](../../reporting-services/report-design/chart-legend-change-item-text-report-builder.md).  
  
##  <a name="WhatsNext"></a> Étape suivante  
 Maintenant que vous avez créé votre premier rapport dans le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)], vous pouvez effectuer les autres didacticiels et commencer à créer des rapports à partir de vos propres données. Pour exécuter le [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)], vous devez avoir l’autorisation d’accéder à vos sources de données, telles que les bases de données, avec une *chaîne de connexion*, qui vous permet de vous connecter à la source de données. Votre administrateur système sera en mesure de vous fournir les informations nécessaires.  
  
 Pour utiliser les autres didacticiels, vous devez le nom d’une instance de SQL Server et les informations d’identification suffisantes pour accéder en lecture seule aux bases de données. Là encore, vous pouvez vous adresser à votre administrateur système.  
  
 Pour finir, afin d'enregistrer vos rapports sur un serveur de rapports ou un site SharePoint intégré à un serveur de rapports, il vous faut posséder l'URL et les autorisations nécessaires. Vous pouvez créer les rapports que vous créez directement à partir de votre ordinateur, mais les rapports procurent davantage de fonctionnalités lorsqu'ils sont exécutés à partir du serveur de rapports ou d'un site SharePoint. Vous devez disposer des autorisations nécessaires pour exécuter vos rapports (ou d'autres rapports) à partir du serveur de rapports ou du site SharePoint sur lequel ils sont publiés. Pour obtenir ces autorisations, contactez votre administrateur système.  
  
 Avant de continuer, il peut être utile de lire certains documents relatifs à certains concepts et termes. Voir [Concepts de création de rapport (Générateur de rapports et SSRS)](../../reporting-services/report-design/report-authoring-concepts-report-builder-and-ssrs.md). Il est également conseillé d'accorder un peu de temps à la planification avant de créer votre premier rapport. Ce temps consacré vous sera utile. Voir [Planification d’un rapport (Générateur de rapports)](../../reporting-services/report-design/planning-a-report-report-builder.md).  

## <a name="next-steps"></a>Étapes suivantes

[Didacticiels du Générateur de rapports](../../reporting-services/report-builder-tutorials.md)   
[Générateur de rapports dans SQL Server 2016](../../reporting-services/report-builder/report-builder-in-sql-server-2016.md)  

D’autres questions ? [Essayez de poser le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
