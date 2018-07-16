---
title: Présentation de DAX dans les modèles tabulaires (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b2693985-1bea-4861-a100-cea4761ba809
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1c4047c082a890e0ddd2871bbd35d7dbd21d363d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37291435"
---
# <a name="understanding-dax-in-tabular-models-ssas-tabular"></a>Fonctionnement de DAX dans les modèles tabulaires (SSAS Tabulaire)
  DAX (Data Analysis Expressions) est le langage de formule utilisé pour créer des calculs personnalisés dans [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour les classeurs Microsoft Excel et les modèles tabulaires de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Les formules DAX comportent des fonctions, des opérateurs, et des valeurs pour effectuer des calculs avancés sur les données des tables et des colonnes.  
  
 Bien que DAX s'applique à la fois aux classeurs et aux projets de modèles tabulaires [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , cette rubrique traite plus précisément des projets de modèles tabulaires créés dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Avant de lire cette rubrique, vous devez avoir une bonne compréhension des modèles tabulaires et de l'environnement de création de projets de modèles tabulaires dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Sections de cette rubrique :  
  
-   [DAX dans les modèles tabulaires](#bkmk_DAXintm)  
  
-   [Formules DAX dans les colonnes calculées, les mesures et les filtres de lignes](#bkmk_DAX)  
  
-   [Types de données DAX](#bkmk_DAX_datatypes)  
  
-   [Opérateurs DAX](#bkmk_DAX_opertors)  
  
-   [Formules DAX](#bkmk_DAX_Formulas)  
  
-   [Fonctions DAX](#bkmk_DAX_functions)  
  
-   [Contexte dans les formules DAX](#bkmk_context)  
  
-   [Formules et modèle tabulaire](#bkmk_RelModel)  
  
-   [Utilisation de tables et de colonnes](#bkmk_tables)  
  
-   [Mise à jour des résultats des formules (processus)](#bkmk_RefreshRecalc)  
  
-   [Résolution des erreurs dans les formules](#bkmk_troubleshoot)  
  
-   [Ressources supplémentaires](#bkmk_addional_resources)  
  
##  <a name="bkmk_DAXintm"></a> DAX dans les modèles tabulaires  
 Dans [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et dans les modèles tabulaires, il n'y a pas de différence fonctionnelle dans la façon dont les formules DAX calculent les valeurs à partir de leurs jeux de données respectifs. Toutefois, l'endroit où les formules DAX sont créées dans les outils de création de classeurs et de modèles est différent, ainsi que l'endroit où le contexte est évalué dans certaines mesures.  
  
 Dans [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], les formules de calcul sont généralement créées par l'utilisateur du classeur dans le cadre de l'analyse décisionnelle en libre-service. Les colonnes calculées sont créées pour une table dans la fenêtre PowerPivot, et les mesures sont créées dans des tableaux croisés dynamiques ou dans la zone de calcul. Contrairement aux projets de modèles tabulaires, les classeurs PowerPivot ne fournissent pas la sécurité basée sur les rôles qui peut utiliser des formules DAX pour sécuriser les données.  
  
 Dans les projets de modèles tabulaires, les formules de calcul sont créées dans le générateur de modèles de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] par les auteurs du modèle. Alors que les valeurs des colonnes calculées à l'aide de formules DAX apparaissent immédiatement dans la table dans le générateur de modèles, à l'exception de la fonctionnalité d'aperçu des mesures dans la grille de mesures, les mesures ne sont pas calculées tant qu'un utilisateur ne spécifie pas un filtre dans un client de création de rapports tel que [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] ou dans des tableaux croisés dynamiques dans Microsoft Excel.  
  
 Si vous importez un classeur PowerPivot dans un projet de modèle tabulaire à l'aide du modèle de projet Importer à partir de PowerPivot, les formules DAX des colonnes calculées sont automatiquement créées dans le nouveau modèle tabulaire. Les formules DAX des mesures implicites et explicites dans le classeur sont automatiquement créées dans le nouveau modèle tabulaire en tant que mesures explicites. Étant donné que les fonctionnalités de rôle et de sécurité du filtre de lignes n'existent pas encore dans les classeurs PowerPivot, vous devez créer au moins un rôle dans le nouveau modèle tabulaire pour fournir aux membres du rôle l'accès aux données du modèle. Les formules DAX dans les filtres de lignes ne sont nécessaires que si vous souhaitez sécuriser les données de table au niveau de la ligne.  
  
##  <a name="bkmk_DAX"></a> Formules DAX dans les colonnes calculées, les mesures et les filtres de lignes  
 Pour les modèles tabulaires créés dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], les formules DAX sont utilisées dans les colonnes calculées, les mesures et les filtres de lignes.  
  
### <a name="calculated-columns"></a>Colonnes calculées  
 Une colonne calculée est une colonne que vous ajoutez à une table existante (dans le concepteur de modèles) et ses valeurs sont définies par la formule DAX créée. Vous créez les formules des colonnes calculées dans le concepteur de modèles à l'aide de la barre de formule.  
  
> [!NOTE]  
>  Les colonnes calculées ne sont pas prises en charge pour les modèles qui récupèrent des données d'une source de données relationnelle à l'aide du mode DirectQuery.  
  
 Lorsqu'une colonne calculée contient une formule DAX valide, les valeurs sont calculées pour chaque ligne dès que la formule est écrite. Les valeurs sont ensuite stockées dans la base de données. Par exemple, dans une table Date, lorsque la formule `=[Calendar Year] & " Q" & [Calendar Quarter]` est entrée dans la barre de formule, la valeur de chaque ligne de la table est calculée en utilisant les valeurs de la colonne Calendar Year (dans la même table Date), en ajoutant un espace et la majuscule Q, puis en ajoutant les valeurs de la colonne Calendar Quarter (dans la même table Date). Le résultat de chaque ligne de la colonne calculée est calculé immédiatement et apparaît, par exemple, comme **2010 Q1**. Les valeurs de la colonne sont recalculées uniquement si les données sont retraitées.  
  
 Pour plus d’informations, consultez [Calculated Columns &#40;SSAS Tabular&#41;](ssas-calculated-columns.md).  
  
### <a name="measures"></a>mesures  
 Les mesures sont des formules dynamiques dont les résultats changent selon le contexte. Les mesures sont utilisées dans les formats de création de rapports qui prennent en charge la combinaison et le filtrage des données de modèle à l'aide de plusieurs attributs, tels qu'un rapport [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] , un tableau croisé dynamique ou un graphique croisé dynamique Excel. Dans les projets de modèles tabulaires, les mesures sont définies par l'auteur du modèle à l'aide de la grille de mesures (et de la barre de formule) dans le concepteur de modèles dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Une formule dans une mesure peut utiliser des fonctions d'agrégation standard créées automatiquement à l'aide de la fonction Somme automatique, telles que COUNT ou SUM, ou vous pouvez définir votre propre formule à l'aide de DAX. Lorsque vous définissez une formule pour une mesure dans la barre de formule, une info-bulle affiche un aperçu rapide de ce que seront les résultats pour l'ensemble du contexte actuel, mais autrement, aucun résultat n'est immédiatement généré. D'autres détails concernant la mesure apparaissent également dans le volet **Propriétés** .  
  
 La raison pour laquelle vous ne pouvez pas voir les résultats (filtrés) du calcul immédiatement tient au fait que le résultat d'une mesure ne peut pas être déterminé sans contexte. Évaluer une mesure requiert une application cliente de création de rapports qui peut fournir le contexte nécessaire pour récupérer les données relatives à chaque cellule, puis évaluer l'expression pour chaque cellule. Ce client peut être un tableau croisé dynamique ou un graphique croisé dynamique Excel, un rapport [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] ou une requête MDX. Indépendamment du client de création de rapports, une requête distincte est exécutée pour chaque cellule dans les résultats. Autrement dit, chaque combinaison d'en-têtes de lignes et de colonnes dans un tableau croisé dynamique, ou chaque sélection de segments et de filtres dans un rapport [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] , génère un sous-ensemble différent de données à partir desquelles la mesure est calculée. Par exemple, dans une mesure avec la formule, `Total Sales:=SUM([Sales Amount])`, lorsqu'un utilisateur place la mesure Total Sales dans la fenêtre Values dans un tableau croisé dynamique et place la colonne Product Category d'une table Product dans la fenêtre de filtres, la somme de Sales Amount est calculée et affichée pour chaque catégorie de produit.  
  
 Contrairement aux colonnes calculées et aux filtres de lignes, la syntaxe d'une mesure inclut le nom de la mesure précédant la formule. Dans l'exemple qui vient d'être donné, le nom, **Total Sales:** apparaît avant la formule. Après avoir créé une mesure, le nom et sa définition s'affichent dans la liste de champs de l'application cliente de génération de rapports et sont disponibles à tous les utilisateurs du modèle selon les perspectives et les rôles.  
  
 Pour plus d’informations, consultez [Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md).  
  
### <a name="row-filters"></a>Filtres de lignes  
 Les filtres de lignes définissent les lignes d'une table qui sont visibles aux membres d'un rôle donné. Les filtres de lignes peuvent être créés pour chaque table dans un modèle à l'aide de formules DAX. Les filtres de lignes sont créés pour un rôle particulier à l'aide du Gestionnaire de rôles dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Les filtres de lignes peuvent également être définis pour un modèle déployé à l'aide des propriétés de rôle dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Dans un filtre de lignes, une formule DAX, qui doit générer une valeur booléenne TRUE/FALSE, définit les lignes qui peuvent être retournées par les résultats d'une requête par les membres de ce rôle particulier. Les lignes non incluses dans la formule DAX ne peuvent pas être retournées. Si nous prenons comme exemple les membres du rôle Sales et la table Customers avec la formule DAX suivante, `=Customers[Country] = “USA”`, les membres du rôle Sales peuvent uniquement afficher les données des clients aux États-unis et les agrégats, tels que SUM, sont retournés uniquement pour ces clients.  
  
 Lorsque vous définissez un filtre de lignes à l'aide d'une formule DAX, vous créez un ensemble de lignes autorisé. Cela interdit pas l'accès à d'autres lignes ; en revanche, elles ne sont pas retournées dans le cadre de l'ensemble de lignes autorisé. D'autres rôles peuvent autoriser l'accès aux lignes exclues par la formule DAX. Si un utilisateur est membre d'un autre rôle, et des filtres de lignes de ce rôle permettent l'accès à cet ensemble de lignes particulier, l'utilisateur peut afficher les données pour cette ligne.  
  
 Les filtres de lignes s'appliquent aux lignes spécifiées ainsi qu'aux lignes connexes. Lorsqu'une table contient plusieurs relations, les filtres appliquent la sécurité de la relation qui est active. Les filtres de lignes se croisent avec d'autres filtres de ligne définis pour les tables associées.  
  
 Pour plus d’informations, consultez [Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).  
  
##  <a name="bkmk_DAX_datatypes"></a> Types de données DAX  
 Vous pouvez importer des données dans un modèle à partir de nombreuses sources de données différentes, qui peuvent prendre en charge des types de données différents. Lorsque vous importez des données dans un modèle, les données sont converties en un des types de données de modèle tabulaire. Quand les données du modèle sont utilisées dans un calcul, les données sont converties en un type de données DAX pour la durée et le résultat du calcul. Lorsque vous créez une formule DAX, les termes utilisés dans la formule déterminent automatiquement le type de données de valeur retournées.  
  
 Les modèles tabulaires, et DAX, prennent en charge les types de données suivants :  
  
|Type de données dans le modèle|Type de données dans DAX|Description|  
|------------------------|----------------------|-----------------|  
|Nombre entier|Valeur entière de 64 bits (huit octets) <sup>1, 2</sup>|Nombres qui n'ont pas de décimales. Les entiers peuvent être des nombres positifs ou négatifs, mais doivent être compris entre -9 223 372 036 854 775 808 (-2^63) et 9 223 372 036 854 775 807 (2^63-1).|  
|Nombre décimal|Nombre réel de 64 bits (huit octets) <sup>1, 2</sup>|Les nombres réels sont des nombres qui peuvent avoir des décimales. Les nombres réels couvrent une large gamme de valeurs :<br /><br /> Valeurs négatives de -1.79E +308 à -2.23E -308<br /><br /> Zéro<br /><br /> Valeurs positives de 2.23E -308 à -1.79E +308<br /><br /> Toutefois, le nombre de bits significatifs est limité à 17 chiffres décimaux.|  
|Booléen|Booléen|Valeur True ou valeur False.|  
|Texte|String|Chaîne de données caractères au format Unicode. Il peut s'agir de chaînes, de nombres ou de dates représentés dans un format texte.|  
|Date|Date/heure|Dates et heures dans une représentation date-heure acceptée.<br /><br /> Les dates valides sont toutes les dates après le 1er mars 1900.|  
|Monétaire (Currency)|Monétaire (Currency)|Le type de données devise autorise des valeurs entre -922 337 203 685 477,5808 et 922 337 203 685 477,5807 avec quatre chiffres décimaux à précision fixe.|  
|Néant|Vide|Le type de données Vide (Blank) de DAX représente et remplace les valeurs Null SQL. Vous pouvez créer une valeur vide à l'aide de la fonction BLANK et tester les valeurs vides à l'aide de la fonction logique ISBLANK.|  
  
 Les modèles tabulaires incluent également le type de données Table comme entrée ou sortie dans de nombreuses fonctions DAX. Par exemple, la fonction FILTER prend une table en entrée et génère en sortie une autre table qui contient uniquement les lignes qui répondent aux conditions de filtre. En associant des fonctions de table à des fonctions d'agrégation, vous pouvez effectuer des calculs complexes sur des jeux de données définis de façon dynamique.  
  
 Bien que les types de données soient généralement définis automatiquement, il est important de comprendre de quelle façon ils s'appliquent, notamment, aux formules DAX. Des erreurs dans les formules ou des résultats inattendus sont notamment dus à l'emploi d'un opérateur spécifique qui ne peut pas être utilisé avec le type de données spécifié dans un argument. Par exemple, la formule `= 1 & 2`, retourne un résultat de chaîne de 12. Toutefois, la formule `= “1” + “2”`retourne un résultat entier de 3.  
  
 Pour plus d’informations sur les types de données dans les modèles tabulaires et les conversions explicites et implicites des types de données dans DAX, consultez [Types de données pris en charge &#40;SSAS tabulaire&#41;](data-types-supported-ssas-tabular.md).  
  
##  <a name="bkmk_DAX_opertors"></a> Opérateurs DAX  
 Le langage DAX utilise quatre types différents d'opérateurs de calcul dans les formules :  
  
-   Opérateurs de comparaison pour comparer des valeurs et retourner une valeur TRUE\FALSE logique.  
  
-   Opérateurs arithmétiques pour effectuer des calculs arithmétiques qui retournent des valeurs numériques.  
  
-   Opérateurs de concaténation de texte pour joindre deux chaînes de texte ou plus.  
  
-   Opérateurs logiques qui combinent deux expressions ou plus pour retourner un résultat unique.  
  
 Pour plus d’informations sur les opérateurs utilisés dans les formules DAX, consultez [référence des opérateurs DAX pour PowerPivot](https://msdn.microsoft.com/library/ee634237(v=sql.120).aspx).  
  
##  <a name="bkmk_DAX_Formulas"></a> Formules DAX  
 Les formules DAX sont essentielles pour créer des calculs dans les colonnes calculées et les mesures, et sécuriser vos données à l'aide de filtres au niveau des lignes. Pour créer des formules pour les colonnes calculées et les mesures, vous utilisez la barre de formule en haut de la fenêtre du concepteur de modèles. Pour créer des formules pour les filtres de lignes, vous utilisez la boîte de dialogue Gestionnaire de rôles. Les informations de cette section sont une mise en route et vous aident à comprendre les aspects fondamentaux des formules DAX.  
  
###  <a name="basics"></a> Concepts de base des formules  
 DAX permet aux créateurs de modèles tabulaires de définir des calculs personnalisés dans les deux tables de modèle, dans le cadre de colonnes calculées, et en tant que mesures associées à des tables mais n'apparaissant pas directement dans celles-ci. DAX permet également aux créateurs de modèles de sécuriser les données en créant des calculs qui retournent une valeur booléenne indiquant quelles lignes dans une table spécifique ou associée peuvent être interrogées par des utilisateurs membres du rôle associé.  
  
 Les formules DAX peuvent être très simples ou assez complexes. Le tableau suivant présente des exemples de formules simples qui peuvent être utilisées dans une colonne calculée.  
  
|||  
|-|-|  
|Formule|Description|  
|`=TODAY()`|Insère la date du jour dans chaque ligne de la colonne.|  
|`=3`|Insère la valeur 3 dans chaque ligne de la colonne.|  
|`=[Column1] + [Column2]`|Ajoute les valeurs dans la même ligne de [Column1] et [Column2] et place les résultats dans la colonne calculée de la même ligne.|  
  
 Que la formule que vous créez soit simple ou complexe, les étapes suivantes vous permettent de la générer :  
  
1.  Chaque formule doit commencer par un signe égal.  
  
2.  Vous pouvez taper ou sélectionner un nom de fonction ou taper une expression.  
  
3.  Commencez par taper les premières lettres de la fonction ou du nom que vous recherchez pour que la saisie semi-automatique affiche une liste des fonctions, tables et colonnes disponibles. Appuyez sur TAB pour ajouter un élément de la liste de saisie semi-automatique dans la formule.  
  
     Vous pouvez aussi cliquer sur le bouton **Fx** pour afficher une liste de fonctions disponibles. Pour sélectionner une fonction dans la liste déroulante, utilisez les touches de direction pour mettre en surbrillance celle de votre choix, puis cliquez sur **OK** pour l'ajouter à la formule.  
  
4.  Fournissez les arguments de la fonction en les sélectionnant dans une liste déroulante de tables et colonnes possibles ou en tapant des valeurs.  
  
5.  Recherchez les éventuelles erreurs de syntaxe : vérifiez que toutes les parenthèses sont fermées, et que les références aux colonnes, tables et valeurs sont correctes.  
  
6.  Appuyez sur Entrée pour accepter la formule.  
  
> [!NOTE]  
>  Dans une colonne calculée, dès que vous acceptez la formule et que la formule est validée, la colonne est remplie avec des valeurs. Dans une mesure, en appuyant sur ENTRÉE vous enregistrez la définition de la mesure dans la grille de mesures de la table. Si une formule n'est pas valide, une erreur sera affichée.  
  
 Dans cet exemple, nous allons nous intéresser à une formule plus complexe dans une mesure nommée Days in Current Quarter :  
  
```  
Days in Current Quarter:=COUNTROWS( DATESBETWEEN( 'Date'[Date], STARTOFQUARTER( LASTDATE('Date'[Date])), ENDOFQUARTER('Date'[Date])))  
```  
  
 Cette mesure est utilisée pour créer un taux de comparaison entre une période incomplète et la période précédente. La formule doit prendre en compte la partie de la période qui s'est écoulée, et la comparer à la même partie de la période précédente. Dans ce cas, [Jours du trimestre en cours à ce jour] /[Jours du trimestre en cours] donne la période écoulée dans la période actuelle.  
  
 Cette formule contient les éléments suivants :  
  
|Élément de formule|Description|  
|---------------------|-----------------|  
|`Days in Current Quarter:=`|Nom de la mesure.|  
|`=`|Le signe égal (=) démarre la formule.|  
|`COUNTROWS`|Le [fonction COUNTROWS &#40;DAX&#41; ](https://msdn.microsoft.com/library/ee634574(v=sql.120).aspx) compte le nombre de lignes dans la table de dates|  
|`()`|Les parenthèses ouvertes et fermées spécifient les arguments.|  
|`DATESBETWEEN`|La fonction DATESBETWEEN retourne les dates entre la dernière date de chaque valeur dans la colonne Date dans la table Date.|  
|`'Date'`|Spécifie la table Date. Les tables sont entre guillemets simples.|  
|`[Date]`|Spécifie la colonne Date dans la table Date. Les colonnes sont entre parenthèses.|  
|`,`||  
|`STARTOFQUARTER`|La fonction STARTOFQUARTER retourne la date du début du trimestre.|  
|`LASTDATE`|La fonction LASTDATE retourne la dernière date du trimestre.|  
|`'Date'`|Spécifie la table Date.|  
|`[Date]`|Spécifie la colonne Date dans la table Date.|  
|`,`||  
|`ENDOFQUARTER`|Fonction ENDOFQUARTER|  
|`'Date'`|Spécifie la table Date.|  
|`[Date]`|Spécifie la colonne Date dans la table Date.|  
  
#### <a name="using-formula-autocomplete"></a>Utilisation de la saisie semi-automatique des formules  
 La barre de formule dans le concepteur de modèles et la fenêtre des filtres de lignes de la formule dans la boîte de dialogue Gestionnaire de rôles possèdent une fonctionnalité de saisie semi-automatique. La saisie semi-automatique vous aide à saisir une syntaxe de formule valide en vous proposant des options pour chaque élément de la formule.  
  
-   Vous pouvez utiliser la saisie semi-automatique des formules au milieu d'une formule existante avec les fonctions imbriquées. Le texte immédiatement avant le point d'insertion est utilisé pour afficher des valeurs dans la liste déroulante, et tout le texte après le point d'insertion reste inchangé.  
  
-   La saisie semi-automatique n'ajoute pas la parenthèse fermante des fonctions, ni ne met automatiquement en correspondance les parenthèses. Vous devez vous assurer que chaque fonction est correcte syntaxiquement ou vous ne pouvez pas enregistrer ni utiliser la formule.  
  
#### <a name="using-multiple-functions-in-a-formula"></a>Utilisation de plusieurs fonctions dans une formule  
 Vous pouvez imbriquer des fonctions, ce qui signifie que vous utilisez les résultats d'une fonction comme un argument d'une autre fonction. Vous pouvez imbriquer jusqu'à 64 niveaux de fonctions dans les colonnes calculées. Toutefois, l'imbrication peut rendre la création ou le dépannage de formules difficile.  
  
 De nombreuses fonctions sont conçues pour être utilisées uniquement comme fonctions imbriquées. Ces fonctions retournent une table, qui ne peut pas être enregistrée directement comme résultat ; elle doit être fournie comme entrée à une fonction de table. Par exemple, les fonctions SUMX, AVERAGEX et MINX requièrent toutes une table comme premier argument.  
  
> [!NOTE]  
>  Certaines limites relatives à l'imbrication de fonctions sont appliquées au sein des mesures ; elles visent à garantir que les performances ne seront pas affectées par les nombreux calculs requis par les dépendances entre colonnes.  
  
##  <a name="bkmk_DAX_functions"></a> Fonctions DAX  
 Cette section fournit une vue d'ensemble des *types* de fonctions pris en charge dans le langage DAX. Pour plus d’informations, consultez [Référence des fonctions DAX](https://msdn.microsoft.com/library/ee634396.aspx).  
  
 DAX inclut plusieurs fonctions que vous pouvez utiliser pour effectuer des calculs à l'aide de dates et d'heures, créer des valeurs conditionnelles, utiliser des chaînes, effectuer des recherches en fonction des relations et itérer sur une table pour effectuer des calculs récursifs. Si vous connaissez les formules Excel, plusieurs de ces fonctions vous seront familières ; toutefois, les formules DAX diffèrent à de nombreux égards. Voici quelques différences de taille :  
  
-   Une fonction DAX fait toujours référence à une table ou une colonne complète. Si vous souhaitez utiliser certaines valeurs particulières d'une table ou colonne, vous pouvez ajouter des filtres à la formule.  
  
-   Si vous devez personnaliser des calculs en fonction de chaque ligne, DAX fournit des fonctions qui vous permettent d'utiliser la valeur de ligne actuelle ou une valeur associée comme genre de paramètre pour effectuer des calculs qui varient selon le contexte. Pour comprendre le fonctionnement de ces fonctions, consultez Contexte dans les formules DAX plus loin dans cette rubrique.  
  
-   DAX inclut de nombreuses fonctions qui retournent une table, plutôt qu'une valeur. La table n'est pas affichée dans un client de création de rapports, mais elle est utilisée pour fournir une entrée à d'autres fonctions. Par exemple, vous pouvez récupérer une table, puis compter les valeurs distinctes qu'elle contient, ou calculer les sommes dynamiques entre les colonnes ou les tables filtrées.  
  
-   Les fonctions DAX intègrent une grande diversité de fonctions *Time Intelligence* . Ces fonctions vous permettent de définir ou de sélectionner des plages de dates, et effectuer des calculs dynamiques basés sur ces dates ou plages. Par exemple, vous pouvez comparer les sommes sur des périodes parallèles.  
  
### <a name="date-and-time-functions"></a>Fonctions de date et d'heure  
 Les fonctions de date et d'heure de DAX sont semblables à celles de Microsoft Excel. Toutefois, les fonctions DAX sont basées sur le `datetime` types de données utilisés par Microsoft SQL Server. Pour plus d’informations, consultez [Date and Time Functions &#40;DAX&#41;](https://msdn.microsoft.com/library/ee634786(v=sql.120).aspx).  
  
### <a name="filter-functions"></a>Fonctions de filtrage  
 Les fonctions de filtrage de DAX permettent de retourner des types de données spécifiques, de rechercher des valeurs dans les tables associées et de procéder à un filtrage par valeurs associées. Les fonctions de recherche s'appuient sur des tables et des relations, comme une base de données. Les fonctions de filtrage vous permettent de manipuler le contexte de données pour créer des calculs dynamiques. Pour plus d’informations, consultez [fonctions de filtre &#40;DAX&#41;](https://msdn.microsoft.com/library/ee634807(v=sql.120).aspx).  
  
### <a name="information-functions"></a>Fonctions d'information  
 Une fonction d'information examine la cellule ou la ligne qui est fournie comme argument et vous indique si la valeur correspond au type attendu. Par exemple, la fonction ISERROR retourne TRUE si la valeur que vous référencez contient une erreur. Pour plus d’informations, consultez [les fonctions d’Information &#40;DAX&#41;](https://msdn.microsoft.com/library/ee634552(v=sql.120).aspx).  
  
### <a name="logical-functions"></a>Fonctions logiques  
 Les fonctions logiques agissent sur une expression pour retourner des informations sur les valeurs au sein de l'expression. Par exemple, la fonction TRUE vous permet de savoir si une expression que vous évaluez retourne une valeur TRUE. Pour plus d’informations, consultez [fonctions logiques &#40;DAX&#41;](https://msdn.microsoft.com/library/ee634365(v=sql.120).aspx).  
  
### <a name="mathematical-and-trigonometric-functions"></a>Fonctions mathématiques et trigonométriques  
 Les fonctions mathématiques dans DAX sont très semblables aux fonctions mathématiques et trigonométriques Excel. Il existe quelques différences mineures dans les types de données numériques utilisés par les fonctions DAX. Pour plus d’informations, consultez [fonctions mathématiques et trigonométriques &#40;DAX&#41;](https://msdn.microsoft.com/library/ee634241(v=sql.120).aspx).  
  
### <a name="statistical-functions"></a>Fonctions statistiques  
 DAX fournit des fonctions statistiques qui effectuent des agrégations. Outre la création de sommes et de moyennes, ou la recherche des valeurs maximale et minimale, il est également possible dans DAX de filtrer une colonne avant agrégation ou de créer des agrégations en fonction des tables associées. Pour plus d’informations, consultez [fonctions statistiques &#40;DAX&#41;](https://msdn.microsoft.com/library/ee634822(v=sql.120).aspx).  
  
### <a name="text-functions"></a>Fonctions de texte  
 Les fonctions de texte dans DAX sont très semblables à leurs équivalents dans Excel. Vous pouvez retourner une partie d'une chaîne, rechercher un texte dans une chaîne ou concaténer des valeurs de chaîne. DAX fournit également des fonctions pour le contrôle des formats pour les dates, les heures et les nombres. Pour plus d’informations, consultez [fonctions de texte &#40;DAX&#41;](https://msdn.microsoft.com/library/ee634938(v=sql.120).aspx).  
  
### <a name="time-intelligence-functions"></a>Fonctions Time Intelligence  
 Les fonctions Time Intelligence fournies dans DAX vous permettent de créer des calculs qui utilisent la connaissance intégrée relative aux calendriers et aux dates. En utilisant des plages de dates et d'heures en association avec des agrégations ou des calculs, vous pouvez générer des comparaisons explicites à travers des périodes comparables pour les ventes, les stocks, etc. Pour plus d’informations, consultez [fonctions Time Intelligence &#40;DAX&#41;](https://msdn.microsoft.com/library/ee634763.aspx).  
  
###  <a name="bkmk_TableFunc"></a> Fonctions table  
 Il existe des fonctions DAX qui génèrent des tables en sortie, qui utilisent des tables en entrée ou les deux à la fois. Étant donné qu'une table peut avoir une colonne unique, les fonctions table utilisent également des colonnes uniques comme entrées. Il importe de savoir utiliser ces fonctions table pour tirer le meilleur parti des formules DAX. DAX inclut les types suivants de fonctions table :  
  
 **Fonctions de filtre** Retournent une colonne, une table ou des valeurs associées à la ligne actuelle.  
  
 **Fonctions d'agrégation** Regroupent toutes les expressions sur les lignes d'une table.  
  
 **Fonctions Time Intelligence** Retournent une table de dates ou utilisent une table de dates pour calculer une agrégation.  
  
##  <a name="bkmk_context"></a> Contexte dans les formules DAX  
 Le*contexte* est un concept qu'il est important de comprendre lorsque vous créez des formules à l'aide de DAX. Le contexte vous permet d'effectuer une analyse dynamique dans la mesure où les résultats d'une formule changent pour refléter la sélection de ligne ou de cellule actuelle, ainsi que toutes les données associées. Il est impératif de comprendre ce qu'est un contexte et de savoir utiliser un contexte à bon escient pour créer des analyses dynamiques performantes et pour résoudre les problèmes dans les formules.  
  
 Les formules dans les modèles tabulaires peuvent être évaluées dans un contexte différent, en fonction d'autres éléments de conception.  
  
-   Filtres appliqués dans un tableau croisé dynamique ou un rapport  
  
-   Filtres définis dans une formule  
  
-   Relations spécifiées à l'aide de fonctions spéciales dans une formule  
  
 Il existe différents types de contexte : *contexte de ligne*, *contexte de requête*et *contexte de filtre*.  
  
###  <a name="bkmk_row_context"></a> Contexte de ligne  
 Le*contexte de ligne* peut être considéré comme la « ligne actuelle ». Si vous créez une formule dans une colonne calculée, le contexte de ligne correspondant à cette formule inclut les valeurs de toutes les colonnes dans la ligne actuelle. Si la table est associée à une autre table, le contenu inclut également toutes les valeurs de cette autre table qui sont mises en relation avec la ligne actuelle.  
  
 Par exemple, supposons que vous créez une colonne calculée, `=[Freight] + [Tax]`, qui additionne les valeurs de deux colonnes, Freight et Tax, de la même table. Cette formule obtient automatiquement les valeurs de la ligne actuelle uniquement dans les colonnes spécifiées.  
  
 Le contexte de ligne suit également toutes les relations définies entre les tables, notamment les relations définies dans une colonne calculée à l'aide de formules DAX, afin de déterminer les lignes des tables liées qui sont associées à la ligne actuelle.  
  
 Par exemple, la formule suivante utilise la fonction RELATED pour extraire une valeur de taxe d'une table associée, selon la région vers laquelle la commande a été expédiée. La valeur de taxe est déterminée par l'utilisation de la valeur de la région dans la table actuelle, la recherche de la région dans la table associée, puis l'obtention du taux d'imposition de cette région à partir de la table associée.  
  
```  
= [Freight] + RELATED('Region'[TaxRate])  
```  
  
 Cette formule obtient le taux d'imposition pour la région active de la table Region et l'ajoute à la valeur de la colonne de Freight. Dans les formules DAX, vous n'avez pas besoin de connaître ou spécifier la relation spécifique qui connecte les tables.  
  
#### <a name="multiple-row-context"></a>Contextes de ligne multiples  
 Le langage DAX (Data Analysis Expressions) inclut des fonctions qui itèrent des calculs sur une table. Ces fonctions peuvent avoir plusieurs lignes actives, chacune avec son propre contexte de ligne.  Fondamentalement, ces fonctions vous permettent de créer des formules qui effectuent des opérations de manière récursive sur une boucle interne et externe.  
  
 Par exemple, supposons que votre modèle contienne une table **Products** et une table **Sales** . Les utilisateurs peuvent vouloir parcourir la totalité de la table Sales, remplie de transactions impliquant plusieurs produits, et rechercher la quantité maximale commandée pour chaque produit dans l'ensemble de ces transactions.  
  
 Avec DAX, vous pouvez générer une formule unique qui retourne la valeur correcte, et les résultats sont automatiquement mis à jour chaque fois que l'utilisateur ajoute des données aux tables.  
  
```  
=MAXX(FILTER(Sales,[ProdKey]=EARLIER([ProdKey])),Sales[OrderQty])  
```  
  
 Pour obtenir une description détaillée de cette formule, consultez le [fonction EARLIER](https://msdn.microsoft.com/library/ee634551(v=sql.120).aspx).  
  
 Pour résumer, la fonction EARLIER stocke le contexte de ligne de l'opération qui a précédé l'opération active. Cette fonction stocke systématiquement en mémoire deux ensembles de contexte : le premier ensemble représente la ligne actuelle pour la boucle interne de la formule, et le second ensemble représente la ligne actuelle pour la boucle externe de la formule. DAX fournit automatiquement les valeurs entre les deux boucles pour vous permettre de créer des agrégats complexes.  
  
####  <a name="bkmk_query_context"></a> Contexte de requête  
 Un*contexte de requête* fait référence au sous-ensemble de données qui est implicitement récupéré pour une formule. Lorsqu'un utilisateur place une mesure ou un autre champ de valeur dans un tableau croisé dynamique ou dans un rapport basé sur un modèle tabulaire, le moteur examine les en-têtes de ligne et de colonne, les segments et les filtres de rapport afin de déterminer le contexte. Ensuite, les requêtes nécessaires sont exécutées sur la source de données pour obtenir le sous-ensemble correct de données, pour effectuer des calculs définis par la formule, puis pour remplir chaque cellule du tableau croisé dynamique ou du rapport. L'ensemble de données récupéré constitue le contexte de requête de chaque cellule.  
  
> [!WARNING]  
>  Dans un modèle qui utilise le mode DirectQuery, le contexte est évalué, puis les opérations sur les ensembles visant à récupérer le sous-ensemble correct de données et calculer les résultats sont converties en instructions SQL. Ces instructions sont ensuite directement exécutées sur la banque de données relationnelle. Par conséquent, bien que la méthode d'obtention des données et de calcul des résultats soit différente, le contexte lui-même ne change pas.  
  
 Étant donné que le contexte change en fonction de l'endroit où vous placez la formule, les résultats de la formule peuvent également changer.  
  
 Par exemple, supposons que vous créiez une formule qui additionne les valeurs de la colonne **Profit** de la table **Sales** : `=SUM('Sales'[Profit])`.  Si vous utilisez cette formule dans une colonne calculée de la table **Sales** , les résultats de la formule seront identiques pour la totalité de la table, car le contexte de requête de la formule correspond toujours à l'ensemble de données complet de la table **Sales** . Les résultats présenteront les bénéfices de la totalité des régions, des produits, des années, etc.  
  
 Toutefois, plutôt que d'obtenir le même résultat des centaines de fois, les utilisateurs préfèrent généralement obtenir le bénéfice d'une année, d'un pays ou d'un produit spécifique, ou le bénéfice d'une combinaison quelconque de ces éléments, puis obtenir un total général.  
  
 Dans un tableau croisé dynamique, le contexte peut être modifié en ajoutant ou en supprimant des en-têtes de colonne et de ligne, et en ajoutant ou en supprimant des segments. Chaque fois que des utilisateurs ajoutent des en-têtes de colonne ou de ligne au tableau croisé dynamique, ils modifient le contexte de requête dans lequel la mesure est évaluée. Les opérations de segmentation et de filtrage affectent également le contexte. Par conséquent, la même formule, utilisée dans une mesure, est évaluée dans un *contexte de requête* différent pour chaque cellule.  
  
####  <a name="bkmk_filter_context"></a> Contexte de filtre  
 Le*contexte de filtre* est l'ensemble de valeurs autorisé dans chaque colonne, ou dans les valeurs récupérées d'une table associée. Des filtres peuvent être appliqués à la colonne dans le concepteur, ou dans la couche de présentation (rapports et tableaux croisés dynamiques). Des filtres peuvent également être définis explicitement par des expressions de filtre dans la formule.  
  
 Un contexte de filtre est ajouté lorsque vous spécifiez des contraintes de filtre sur l'ensemble de valeurs autorisé dans une colonne ou une table, en utilisant les arguments d'une formule. Un contexte de filtre s'applique au-dessus des autres contextes, tels qu'un contexte de ligne ou un contexte de requête.  
  
 Dans des modèles tabulaires, plusieurs méthodes s'offrent à vous pour créer le contexte de filtre. Dans le contexte de clients qui peuvent consommer le modèle, tels que les rapports [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] , les utilisateurs peuvent créer des filtres à la volée en ajoutant des segments ou des filtres de rapport sur les en-têtes de ligne et de colonne. Vous pouvez également spécifier des expressions de filtre directement dans la formule, pour spécifier des valeurs associées, filtrer les tables utilisées comme entrées ou obtenir de façon dynamique le contexte des valeurs utilisées dans les calculs. Vous pouvez également supprimer entièrement les filtres ou les effacer de manière sélective sur des colonnes spécifiques. C'est très utile lors de la création de formules qui calculent des totaux généraux.  
  
 Pour plus d’informations sur la création de filtres dans des formules, consultez le [fonction de filtre](https://msdn.microsoft.com/library/ee634966(v=sql.120).aspx).  
  
 Pour obtenir un exemple de procédure de suppression de filtres pour créer des totaux généraux, consultez le [fonction ALL](https://msdn.microsoft.com/library/ee634802(v=sql.120).aspx).  
  
 Pour obtenir des exemples montrant comment sélective et d’appliquer des filtres dans des formules, consultez le [fonction ALLEXCEPT](https://msdn.microsoft.com/library/ee634795(v=sql.120).aspx).  
  
####  <a name="bkmk_determine_context"></a> Détermination du contexte dans des formules  
 Lorsque vous créez une formule DAX, la formule est d'abord testée pour vérifier si la syntaxe est valide, puis pour vérifier que les noms des colonnes et des tables inclus dans la formule figurent dans le contexte actuel. Si aucune colonne ou table spécifiée par la formule ne peut être trouvée, une erreur est retournée.  
  
 Le contexte au cours de la validation (et des opérations de recalcul) est déterminé comme décrit dans les sections précédentes, à l'aide des tables disponibles dans le modèle, des relations entre les tables et des éventuels filtres qui ont été appliqués.  
  
 Par exemple, si vous venez d’importer des données dans une nouvelle table et que celle-ci n’est pas associée à d’autres tables (et que vous n’avez pas appliqué de filtres), le *contexte actuel* correspond à l’ensemble entier de colonnes dans la table. Si la table est liée par des relations à d'autres tables, le contexte actuel inclut les tables associées. Si vous ajoutez une colonne de la table à un rapport qui contient des segments et éventuellement certains filtres de rapport, le contexte de la formule correspond au sous-ensemble de données dans chaque cellule du rapport.  
  
 Le contexte est un concept puissant qui peut également compliquer la résolution des problèmes liés aux formules. Nous vous recommandons de commencer par des formules et des relations simples pour voir comment le contexte s'exécute. La section suivante fournit quelques exemples d'utilisation de différents types de contextes par les formules pour un retour dynamique des résultats.  
  
##### <a name="examples-of-context-in-formulas"></a>Exemples de contexte dans les formules  
  
1.  Le [fonction RELATED](https://msdn.microsoft.com/library/ee634202(v=sql.120).aspx) développe le contexte de la ligne actuelle pour inclure des valeurs dans une colonne associée. Cela vous permet d'effectuer des recherches. L'exemple utilisé dans cette rubrique illustre l'interaction du filtrage et du contexte de ligne.  
  
2.  Le [fonction de filtre](https://msdn.microsoft.com/library/ee634966(v=sql.120).aspx) vous permet de spécifier les lignes à inclure dans le contexte actuel. Les exemples utilisés dans cette rubrique illustrent également la façon d'incorporer des filtres dans d'autres fonctions qui effectuent des agrégations.  
  
3.  Le [fonction ALL](https://msdn.microsoft.com/library/ee634802(v=sql.120).aspx) définit le contexte dans une formule. Vous pouvez l'utiliser pour remplacer les filtres qui sont appliqués comme résultat du contexte de requête.  
  
4.  Le [fonction ALLEXCEPT](https://msdn.microsoft.com/library/ee634795(v=sql.120).aspx) vous permet de supprimer tous les filtres, sauf une que vous spécifiez. Les deux rubriques incluent des exemples qui vous guident pas à pas dans la création de formules et l'analyse de contextes complexes.  
  
5.  Le [fonction EARLIER](https://msdn.microsoft.com/library/ee634551(v=sql.120).aspx) et [fonction EARLIEST](https://msdn.microsoft.com/library/ee634779(v=sql.120).aspx) permettent d’effectuer une boucle sur des tables en effectuant des calculs, tout en référençant une valeur à partir d’une boucle interne. Si vous êtes familier des concepts de récursivité et de boucles internes et externes, vous apprécierez la puissance des fonctions EARLIER et EARLIEST. Si ces concepts vous sont étrangers, suivez scrupuleusement les différentes étapes de l'exemple pour comprendre la façon dont les contextes internes et externes sont utilisés dans les calculs.  
  
##  <a name="bkmk_RelModel"></a> Formules et modèle tabulaire  
 Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], le générateur de modèles est une zone où vous pouvez travailler avec plusieurs tables de données et connecter les tables au sein d'un modèle tabulaire. Dans ce modèle, les tables sont jointes par des relations sur les colonnes comportant des valeurs communes (clés). Le modèle tabulaire vous permet de lier des valeurs aux colonnes d'autres tables et créer ainsi des calculs plus intéressants. Comme dans une base de données relationnelle, vous pouvez connecter plusieurs niveaux de tables associées et utiliser des colonnes de n'importe quelle table dans les résultats.  
  
 Par exemple, vous pouvez lier une table de vente, une table de produits et une table de catégories de produit, puis utiliser différentes combinaisons de colonnes dans les tableaux croisés dynamiques et les rapports. Les champs associés peuvent être utilisés pour filtrer les tables connectées, ou pour créer des calculs sur les sous-ensembles. (Si vous n’êtes pas familiarisé avec les bases de données relationnelles et l’utilisation des tables et jointures, consultez [Relations &#40;SSAS tabulaire&#41;](relationships-ssas-tabular.md).)  
  
 Les modèles tabulaires prennent en charge plusieurs relations entre les tables. Pour éviter toute confusion ou des résultats incorrects, une seule relation à la fois est désignée comme la relation active, mais vous pouvez modifier la relation active, si nécessaire, pour parcourir différentes connexions dans les données des calculs. Le [fonction USERELATIONSHIP &#40;DAX&#41; ](https://msdn.microsoft.com/library/hh230952(v=sql.120).aspx) peut être utilisé pour spécifier une ou plusieurs relations à utiliser dans un calcul spécifique.  
  
 Dans un modèle tabulaire, vous devez observer les règles de création de formule suivantes :  
  
-   Lorsque les tables sont connectées par une relation, vous devez vous assurer que les deux colonnes utilisées comme clés ont des valeurs qui correspondent. L'intégrité référentielle n'est toutefois pas appliquée strictement ; par conséquent, il est possible d'avoir des valeurs sans correspondance dans une colonne clé et pour autant de créer une relation. Si cela se produit, vous devez savoir que des valeurs vides ou sans correspondance peuvent affecter les résultats des formules.  
  
-   Lorsque vous liez des tables dans votre modèle à l'aide de relations, vous agrandissez l'étendue, ou le *contexte*, dans laquelle vos formules sont évaluées. Des modifications dans le contexte résultant de l'ajout de nouvelles tables, de nouvelles relations ou de modifications de la relation active peuvent entraîner des modifications de vos résultats qu'il n'est pas possible d'anticiper. Pour plus d'informations, consultez [Contexte dans les formules DAX](#bkmk_context) plus haut dans cette rubrique.  
  
##  <a name="bkmk_tables"></a> Utilisation de tables et de colonnes  
 Les tables des modèles tabulaires sont similaires aux tables Excel, mais différentes dans la manière dont elles fonctionnent avec les données et les formules :  
  
-   Les formules fonctionnent uniquement avec les tables et les colonnes, et non avec les cellules individuelles, les références de plage ou les tableaux.  
  
-   Les formules peuvent utiliser des relations pour obtenir des valeurs à partir de tables associées. Les valeurs récupérées sont toujours associées à la valeur de ligne actuelle.  
  
-   Vous ne pouvez pas avoir de données irrégulières ou « déséquilibrées », comme vous le pouvez dans une feuille de calcul Excel. Chaque ligne d'une table doit contenir le même nombre de colonnes. Toutefois, certaines colonnes peuvent comporter des valeurs vides. Les tables de données Excel et les tables de données de modèle tabulaire ne sont pas interchangeables.  
  
-   Un type de données étant défini pour chaque colonne, toutes les valeurs de cette colonne doivent être du même type.  
  
### <a name="referring-to-tables-and-columns-in-formulas"></a>Référence aux tables et aux colonnes dans les formules  
 Vous pouvez faire référence à toute table et colonne à l'aide de son nom. Par exemple, la formule suivante indique comment faire référence aux colonnes de deux tables à l'aide du nom *complet* :  
  
```  
=SUM('New Sales'[Amount]) + SUM('Past Sales'[Amount])  
```  
  
 Lorsqu'une formule est évaluée, le générateur de modèles vérifie en premier la syntaxe générale, puis il contrôle les noms des colonnes et des tables que vous fournissez par rapport aux colonnes et tables possibles dans le contexte actuel. Si le nom est ambigu ou si la colonne/la table est introuvable, vous obtiendrez une erreur dans votre formule (une #chaîne ERROR au lieu d'une valeur de données dans les cellules où l'erreur se produit). Pour plus d’informations sur les exigences d’affectation de noms des tables, colonnes et autres objets, consultez « Exigences d’affectation de noms » dans [DAX Syntax Specification for PowerPivot](https://msdn.microsoft.com/library/ee634217(v=sql.120).aspx).  
  
### <a name="table-relationships"></a>Relations entre les tables  
 En créant des relations entre les tables, vous avez la possibilité de rechercher des données dans une autre table et d'utiliser les valeurs associées pour effectuer des calculs complexes. Par exemple, vous pouvez utiliser une colonne calculée pour rechercher tous les enregistrements de navigation associés au revendeur actuel, puis additionner les coûts d'expédition pour chacun. Dans de nombreux cas, toutefois, il est possible qu'une relation ne soit pas nécessaire. Vous pouvez utiliser la fonction LOOKUPVALUE dans une formule pour retourner la valeur dans *result_columnName* pour la ligne répondant aux critères spécifiés dans les paramètres *search_column* et *search_value* .  
  
 De nombreuses fonctions DAX requièrent l'existence d'une relation entre les tables ou entre plusieurs tables, afin de localiser les colonnes que vous avez référencées et de retourner des résultats qui ont un sens. D'autres fonctions essaient d'identifier la relation ; toutefois, lorsque cela est possible, créez une relation pour optimiser les résultats. Pour plus d’informations, consultez [Formules et modèle tabulaire](#bkmk_RelModel) plus haut dans cette rubrique.  
  
##  <a name="bkmk_RefreshRecalc"></a> Mise à jour des résultats des formules (processus)  
 Le*traitement des données* et le *recalcul* sont deux opérations distinctes mais liées. Vous devez comprendre en détail ces concepts lorsque vous concevez un modèle qui contient des formules complexes, de grandes quantités de données ou des données obtenues de sources de données externes.  
  
 Le*traitement des données* est le processus de mise à jour des données dans un modèle avec de nouvelles données issues d'une source de données externe.  
  
 Le*recalcul* est le processus de mise à jour des résultats des formules afin de refléter toutes les modifications qui leur ont été apportées, ainsi que toutes les modifications des données sous-jacentes. Le recalcul peut affecter les performances des façons suivantes :  
  
-   Les valeurs dans une colonne calculée sont calculées et stockées dans le modèle. Pour mettre à jour les valeurs dans la colonne calculée, vous devez traiter le modèle à l'aide de l'une des trois commandes de traitement – Traiter entièrement, Traiter les données ou Traiter le recalcul. Le résultat de la formule doit toujours être recalculé, pour la colonne entière, chaque fois que vous modifiez la formule.  
  
-   Les valeurs calculées par des mesures sont dynamiquement évaluées chaque fois qu'un utilisateur ajoute la mesure à un tableau croisé dynamique ou ouvre un rapport. Lorsque l'utilisateur modifie le contexte, les valeurs retournées par la mesure changent. Les résultats de la mesure reflètent toujours les valeurs les plus récentes dans le cache en mémoire.  
  
 Le traitement et le recalcul n'ont aucun effet sur les formules de filtre de lignes à moins que le résultat d'un nouveau calcul retourne une valeur différente, ce qui rend la ligne interrogeable ou non interrogeable par les membres du rôle.  
  
 Pour plus d’informations, consultez [Traiter les données &#40;SSAS tabulaire&#41;](../process-data-ssas-tabular.md).  
  
##  <a name="bkmk_troubleshoot"></a> Résolution des erreurs dans les formules  
 Si vous obtenez une erreur lorsque vous définissez une formule, la formule peut contenir une *erreur syntaxique*, une *erreur sémantique*ou une *erreur de calcul*.  
  
 Les erreurs syntactiques sont les plus faciles à résoudre. Elles impliquent en général une virgule ou une parenthèse manquante. Pour obtenir de l’aide sur la syntaxe d’une fonction, consultez [Référence des fonctions DAX](https://msdn.microsoft.com/library/ee634396.aspx).  
  
 L'autre type d'erreur se produit lorsque la syntaxe est correcte, mais que la valeur ou la colonne référencée n'a pas de sens dans le contexte de la formule. De telles erreurs sémantiques et de calcul peuvent être provoquées par l'un des problèmes suivants :  
  
-   La formule fait référence à une colonne, une table ou une fonction non existante.  
  
-   La formule semble être correcte, mais lorsque le moteur de données extrait les données, il trouve une incompatibilité de type et génère une erreur.  
  
-   La formule passe un nombre ou un type de paramètres incorrect à une fonction.  
  
-   La formule fait référence à une colonne différente qui comporte une erreur, et par conséquent, ses valeurs ne sont pas valides.  
  
-   La formule fait référence à une colonne qui n'a pas été traitée, ce qui signifie qu'elle comporte des métadonnées, mais aucune donnée à proprement parler à utiliser pour les calculs.  
  
 Dans les quatre premiers cas, DAX signale la colonne entière qui contient la formule non valide. Dans le dernier cas, DAX grise la colonne pour indiquer que la colonne se trouve dans un état non traité.  
  
##  <a name="bkmk_addional_resources"></a> Ressources supplémentaires  
 La rubrique [Modélisation tabulaire &#40;didacticiel Adventure Works&#41;](../tabular-modeling-adventure-works-tutorial.md) fournit des instructions pas à pas pour créer un modèle tabulaire incluant de nombreux calculs dans des colonnes calculées, des mesures et des filtres de lignes. Pour la plupart des formules, une description de la fonction est fournie.  
  
 Le [Analysis Services et le Blog de l’équipe PowerPivot](http://go.microsoft.com/fwlink/?LinkID=220949&clcid=0x409) fournit des informations, des conseils, des actualités et annonces sur [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] et PowerPivot.  
  
 Le [Centre de ressources DAX](http://go.microsoft.com/fwlink/?LinkID=220966&clcid=0x409) fournit des informations internes et externes sur DAX, notamment de nombreuses solutions DAX soumises par des professionnels Business Intelligence.  
  
## <a name="see-also"></a>Voir aussi  
 [Data Analysis Expressions &#40;DAX&#41; référence](https://msdn.microsoft.com/library/gg413422(v=sql.120).aspx)   
 [Mesures &#40;SSAS tabulaire&#41;](measures-ssas-tabular.md)   
 [Colonnes calculées &#40;SSAS tabulaire&#41;](ssas-calculated-columns.md)   
 [Rôles &#40;SSAS tabulaire&#41;](roles-ssas-tabular.md)   
 [Indicateurs de performance clés &#40;SSAS tabulaire&#41;](kpis-ssas-tabular.md)   
 [Sources de données prises en charge &#40;SSAS Tabulaire&#41;](data-sources-supported-ssas-tabular.md)  
  
  
