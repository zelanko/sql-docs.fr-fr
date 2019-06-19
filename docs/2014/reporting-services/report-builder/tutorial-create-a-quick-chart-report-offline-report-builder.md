---
title: 'Tutoriel : Créer un rapport de graphique rapide en mode hors connexion (Générateur de rapports) | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports, creating
- tutorials, getting started
- creating reports
ms.assetid: 6b1db67a-cf75-494c-b70c-09f1e6a8d414
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f345eaa2a51b5e6789f2a03968f8a1e68b12519a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66107569"
---
# <a name="tutorial-create-a-quick-chart-report-offline-report-builder"></a>Tutoriel : Créer un rapport de graphique rapide en mode hors connexion (Générateur de rapports)
  Dans ce didacticiel, vous allez créer un graphique à secteurs à l'aide d'un Assistant, puis le modifier quelque peu afin d'obtenir un petit aperçu des opérations réalisables. Vous pouvez effectuer ce didacticiel de deux façons différentes. Les deux méthodes ont le même résultat, un graphique à secteurs comme celui de l’illustration suivante :  
  
 ![« Mon premier graphique à secteurs « à exécution afficher](../media/rs-my1stpierunview.gif "mon premier graphique à secteurs dans la vue de l’exécution")  
  
## <a name="prerequisites"></a>Prérequis  
 Que vous utilisiez des données XML ou une requête [!INCLUDE[tsql](../../../includes/tsql-md.md)], vous devez avoir accès au Générateur de rapports [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Vous pouvez exécuter la version autonome ou la version ClickOnce disponible à partir du Gestionnaire de rapports ou d'un site SharePoint. Seule la première étape, l'ouverture du Générateur de rapports, est différente pour les versions ClickOnce. Pour plus d’informations, consultez [installation, désinstallation et prise en charge du Générateur de rapports](../install-uninstall-and-report-builder-support.md).  
  
##  <a name="TwoWays"></a> Deux façons de réaliser ce didacticiel  
  
-   [Créer le graphique à secteurs avec des données XML](#CreatePieChartXML)  
  
-   [Créer le graphique à secteurs avec une requête Transact-SQL qui contient des données](#CreatePieQueryData)  
  
### <a name="using-xml-data-for-this-tutorial"></a>Utilisation de données XML pour ce didacticiel  
 Vous pouvez utiliser des données XML que vous copiez à partir de cette rubrique et que vous collez dans l'Assistant. Vous n'avez pas besoin de vous connecter à un serveur de rapports ou un serveur de rapports en mode intégré SharePoint, et vous n'avez pas besoin d'accéder à une instance de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 [Créer le graphique à secteurs avec des données XML](#CreatePieChartXML)  
  
### <a name="using-a-transact-sql-query-that-contains-data-for-this-tutorial"></a>Utilisation d'une requête Transact-SQL qui contient les données de ce didacticiel  
 Vous pouvez copier une requête comprenant des données incluses à partir de cette rubrique et la coller dans l'Assistant. Vous avez besoin du nom d'une instance de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] et d'informations d'identification suffisantes pour accéder en lecture seule aux bases de données. La requête de dataset du didacticiel utilise des données littérales, mais la requête doit être traitée par une instance de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] pour retourner les métadonnées nécessaires à un dataset de rapport.  
  
 L'avantage lié à l'utilisation de la requête [!INCLUDE[tsql](../../../includes/tsql-md.md)] vient du fait que tous les autres didacticiels du Générateur de rapports utilisent la même méthode ; par conséquent, lorsque vous effectuerez d'autres didacticiels, vous saurez déjà quoi faire.  
  
 La requête [!INCLUDE[tsql](../../../includes/tsql-md.md)] requiert quelques conditions préalables supplémentaires. Pour plus d’informations, voir [Éléments requis pour les didacticiels (Générateur de rapports)](../report-builder-tutorials.md).  
  
 [Créer le graphique à secteurs avec une requête Transact-SQL qui contient des données](#CreatePieQueryData)  
  
## <a name="also-in-this-article"></a>Également dans cet article  
 [Après avoir exécuté l’Assistant](#AfterWizard)  
  
 [Quelle est la suite](#WhatsNext)  
  
##  <a name="CreatePieChartXML"></a> Création du graphique à secteurs avec des données XML  
  
#### <a name="to-create-the-pie-chart-with-xml-data"></a>Pour créer le graphique à secteurs avec des données XML  
  
1.  Cliquez sur **Démarrer**, pointez sur **Programmes**, sur **Générateur de rapports Microsoft SQL Server 2012**, puis cliquez sur **Générateur de rapports version**.  
  
     La boîte de dialogue **Mise en route** s'affiche.  
  
    > [!NOTE]  
    >  Si le **mise en route** boîte de dialogue n’apparaît pas, à partir de la **le Générateur de rapports** bouton, cliquez sur **New**.  
  
2.  Dans le volet gauche, assurez-vous que **Rapport** est sélectionné.  
  
3.  Dans le volet droit, cliquez sur **Assistant Graphique**, puis sur **Créer**.  
  
4.  Dans la page **Choisir un dataset** , cliquez sur **Créer un dataset**, puis sur **Suivant**.  
  
5.  Dans la page **Choisir une connexion à une source de données** , cliquez sur **Nouveau**.  
  
     La boîte de dialogue **Propriétés de la source de données** s'ouvre.  
  
6.  Vous pouvez attribuer à la source de données le nom de votre choix. Dans la zone **Nom** , tapez **MonGraphiqueàSecteurs**.  
  
7.  Dans le **sélectionner le type de connexion** , cliquez sur **XML.**  
  
8.  Cliquez sur l’onglet **Informations d’identification** et sélectionnez **Utiliser l’utilisateur Windows actuel. Délégation Kerberos peut être nécessaire**, puis cliquez sur **OK**.  
  
9. Dans la page **Choisir une connexion à une source de données** , cliquez sur **MonGraphiqueàSecteurs**, puis sur **Suivant**.  
  
10. Copiez le texte suivant et collez-le dans la grande zone située au centre de la **concevoir une requête** page.  
  
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
  
11. (Facultatif) Cliquez sur le bouton Exécuter ( **!** ) pour voir les données sur lesquelles votre graphique sera basé.  
  
12. Cliquer sur **Suivant**.  
  
13. Dans la page **Choisir un type de graphique** , cliquez sur **Secteurs**, puis sur **Suivant**.  
  
14. Dans la page **Organiser les champs du graphique**, double-cliquez sur le champ **Sales** dans la zone **Champs disponibles**.  
  
     Notez que ce champ est déplacé automatiquement vers la zone **Valeurs** , car il s'agit d'une valeur numérique.  
  
15. Faites glisser le champ **FullName** de la zone **Champs disponibles** vers la zone **Catégories** (ou double-cliquez dessus pour le faire passer dans la zone **Catégories**), puis cliquez sur **Suivant**.  
  
16. Dans le **choisir un style** page, **océan** est sélectionnée par défaut. Cliquez sur les autres styles pour voir à quoi ils ressemblent.  
  
17. Cliquez sur **Terminer**.  
  
     Votre nouveau graphique à secteurs est maintenant affiché sur l'aire de conception. Il ne s'agit que d'une représentation. La légende indique Full Name 1, Full Name 2, etc., plutôt que les noms des agents commerciaux, et la taille des secteurs du graphique est incorrecte. Cela vous donne néanmoins une idée de l'aspect qu'aura votre rapport.  
  
18. Pour afficher votre graphique à secteurs, cliquez sur **Exécuter** sous l'onglet **Accueil** du ruban.  
  
 ![Icône de flèche utilisée avec le lien Retour au début](../../2014-toc/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour au début") [Retour au début](#TwoWays)  
  
##  <a name="CreatePieQueryData"></a> Création du graphique à secteurs avec une requête [!INCLUDE[tsql](../../../includes/tsql-md.md)]  
  
#### <a name="to-create-the-pie-chart-with-a-includetsqlincludestsql-mdmd-query-that-contains-data"></a>Pour créer le graphique à secteurs avec une requête [!INCLUDE[tsql](../../../includes/tsql-md.md)] qui contient des données  
  
1.  Cliquez sur **Démarrer**, pointez sur **Programmes**, sur **Générateur de rapports Microsoft SQL Server 2012**, puis cliquez sur **Générateur de rapports version**.  
  
2.  Dans le **nouveau rapport ou dataset** boîte de dialogue, vérifiez que **rapport** est sélectionné dans le volet gauche.  
  
3.  Dans le volet droit, cliquez sur **Assistant Graphique**, puis sur **Créer**.  
  
4.  Dans la page **Choisir un dataset** , cliquez sur **Créer un dataset**, puis sur **Suivant**.  
  
5.  Dans la page **Choisir une connexion à une source de données** , sélectionnez une source de données existante ou naviguez jusqu'au serveur de rapports, sélectionnez une source de données, puis cliquez sur **Suivant**. Vous devrez peut-être entrer un nom d'utilisateur et un mot de passe.  
  
    > [!NOTE]  
    >  La source de données que vous choisissez n'a pas d'importance, tant que vous disposez des autorisations appropriées. Vous n'allez pas récupérer de données à partir de la source de données. Pour plus d’informations, voir [Éléments requis pour les didacticiels (Générateur de rapports)](../report-builder-tutorials.md).  
  
6.  Dans la page **Créer une requête** , cliquez sur **Modifier en tant que texte**.  
  
7.  Collez la requête suivante dans le volet de requête :  
  
    ```  
    SELECT 150 AS Sales, 'Jae Pak' AS FullName   
    UNION SELECT 350 AS Sales, 'Jillian Carson' AS FullName   
    UNION SELECT 250 AS Sales, 'Linda C Mitchell' AS FullName   
    UNION SELECT 500 AS Sales, 'Michael Blythe' AS FullName   
    UNION SELECT 450 AS Sales, 'Ranjit Varkey' AS FullName   
    ```  
  
8.  (Facultatif) Cliquez sur le bouton Exécuter ( **!** ) pour voir les données sur lesquelles votre graphique sera basé.  
  
9. Cliquer sur **Suivant**.  
  
10. Dans la page **Choisir un type de graphique** , cliquez sur **Secteurs**, puis sur **Suivant**.  
  
11. Dans la page **Organiser les champs du graphique**, double-cliquez sur le champ **Sales** dans la zone **Champs disponibles**.  
  
     Notez que ce champ est déplacé automatiquement vers la zone **Valeurs** , car il s'agit d'une valeur numérique.  
  
12. Faites glisser le champ **FullName** de la zone **Champs disponibles** vers la zone **Catégories** (ou double-cliquez dessus pour le faire passer dans la zone **Catégories**), puis cliquez sur **Suivant**.  
  
13. Dans la page **Choisir un style** , Océan est sélectionné par défaut. Cliquez sur les autres styles pour voir à quoi ils ressemblent.  
  
14. Cliquez sur **Terminer**.  
  
     Votre nouveau graphique à secteurs est maintenant affiché sur l'aire de conception. Il ne s'agit que d'une représentation. La légende indique Full Name 1, Full Name 2, etc., plutôt que les noms des agents commerciaux, et la taille des secteurs du graphique est incorrecte. Cela vous donne néanmoins une idée de l'aspect qu'aura votre rapport.  
  
15. Pour afficher votre graphique à secteurs, cliquez sur **Exécuter** sous l'onglet **Accueil** du ruban.  
  
 ![Icône de flèche utilisée avec le lien Retour au début](../../2014-toc/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour au début") [Retour au début](#TwoWays)  
  
##  <a name="AfterWizard"></a> Après l'exécution de l'Assistant  
 Maintenant que vous avez créé votre rapport de graphique à secteurs, vous pouvez le manipuler. Sous l'onglet **Exécuter** du ruban, cliquez sur **Conception**de manière à pouvoir continuer de le modifier.  
  
### <a name="make-the-chart-bigger"></a>Augmenter la taille du graphique  
 Vous pouvez augmenter la taille du graphique à secteurs. Cliquez sur le graphique (mais pas sur l'un de ses éléments) pour le sélectionner et faites glisser le coin inférieur droit pour le redimensionner.  
  
### <a name="add-a-report-title"></a>Ajouter un titre de rapport  
 Sélectionnez les mots **Titre du graphique** en haut du graphique, puis tapez un titre, par exemple : **Graphique à secteurs des ventes**.  
  
### <a name="add-percentages"></a>Ajouter des pourcentages  
  
##### <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a>Pour afficher des valeurs en pourcentage sous forme d'étiquettes sur un graphique à secteurs  
  
1.  Avec le bouton droit sur le graphique à secteurs et sélectionnez **afficher les étiquettes de données**. Les étiquettes de données doivent apparaître dans chaque secteur du graphique.  
  
2.  Avec le bouton droit sur les étiquettes et sélectionnez **propriétés de l’étiquette série**. La boîte de dialogue **Propriétés de l'étiquette de la série** s'affiche.  
  
3.  Type `#PERCENT{P0}` pour le **données de l’étiquette** option.  
  
     `{P0}` indique le pourcentage sans décimales. Si vous tapez simplement `#PERCENT`, vos chiffres comporteront deux décimales. `#PERCENT` est un mot clé qui effectue un calcul ou une fonction pour vous ; il en existe de nombreux autres.  
  
 Pour plus d’informations sur la personnalisation des étiquettes et légendes de graphique, voir [Afficher des valeurs en pourcentage dans un graphique à secteurs (Générateur de rapports et SSRS)](../report-design/display-percentage-values-on-a-pie-chart-report-builder-and-ssrs.md) et [Modifier le texte d’un élément de légende (Générateur de rapports et SSRS)](../report-design/chart-legend-change-item-text-report-builder.md).  
  
 ![Icône de flèche utilisée avec le lien Retour au début](../../2014-toc/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour au début") [Retour au début](#TwoWays)  
  
##  <a name="WhatsNext"></a> Étape suivante  
 Maintenant que vous avez créé votre premier rapport dans le Générateur de rapports, vous pouvez effectuer les autres didacticiels et commencer à créer des rapports à partir de vos propres données. Pour exécuter le Générateur de rapports, vous devez avoir l’autorisation d’accéder à vos sources de données, telles que des bases de données, avec un *chaîne de connexion*, ce qui permet de vous connecter à la source de données. Votre administrateur système sera en mesure de vous fournir les informations nécessaires.  
  
 Pour utiliser les autres didacticiels, vous avez besoin du nom d'une instance de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] et d'informations d'identification suffisantes pour accéder en lecture seule aux bases de données. Là encore, vous pouvez vous adresser à votre administrateur système.  
  
 Pour finir, afin d'enregistrer vos rapports sur un serveur de rapports ou un site SharePoint intégré à un serveur de rapports, il vous faut posséder l'URL et les autorisations nécessaires. Vous pouvez créer les rapports que vous créez directement à partir de votre ordinateur, mais les rapports procurent davantage de fonctionnalités lorsqu'ils sont exécutés à partir du serveur de rapports ou d'un site SharePoint. Vous devez disposer des autorisations nécessaires pour exécuter vos rapports (ou d'autres rapports) à partir du serveur de rapports ou du site SharePoint sur lequel ils sont publiés. Pour obtenir ces autorisations, contactez votre administrateur système.  
  
 Avant de continuer, il peut être utile de lire certains documents relatifs à certains concepts et termes. Pour plus d’informations, consultez [Concepts de création de rapport &#40;Générateur de rapports et SSRS&#41;](../report-design/report-authoring-concepts-report-builder-and-ssrs.md). Il est également conseillé d'accorder un peu de temps à la planification avant de créer votre premier rapport. Ce temps consacré vous sera utile. Pour plus d’informations, consultez [planification d’un rapport &#40;Générateur de rapports&#41;](../report-design/planning-a-report-report-builder.md).  
  
 ![Icône de flèche utilisée avec le lien Retour au début](../../2014-toc/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour au début") [Retour au début](#TwoWays)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiels &#40;Générateur de rapports&#41;](../report-builder-tutorials.md)   
 [Générateur de rapports dans SQL Server 2014](report-builder-in-sql-server-2016.md)  
  
  
