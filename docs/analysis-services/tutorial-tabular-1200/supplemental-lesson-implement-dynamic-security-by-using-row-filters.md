---
title: Implémenter la sécurité dynamique à l’aide de filtres de lignes | Microsoft Docs
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dfc217b3a4e5fa58b171677c2acedc313a090285
ms.sourcegitcommit: a6949111461eda0cc9a71689f86b517de3c5d4c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263358"
---
# <a name="supplemental-lesson---implement-dynamic-security-by-using-row-filters"></a>Leçon supplémentaire - implémenter la sécurité dynamique à l’aide de filtres de lignes
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

Dans cette leçon supplémentaire, vous allez créer un rôle supplémentaire qui implémente la sécurité dynamique. La sécurité dynamique permet de définir la sécurité de niveau ligne en fonction du nom d'utilisateur ou de l'ID de connexion de l'utilisateur actuellement connecté. Pour plus d’informations, consultez [Rôles](../tabular-models/roles-ssas-tabular.md).  
  
Pour implémenter la sécurité dynamique, vous devez ajouter une table à votre modèle qui contient les noms des utilisateurs Windows qui peuvent créer une connexion au modèle comme source de données et parcourir les objets de modèle et les données. Le modèle que vous allez créer à l'aide de ce didacticiel est dans le contexte d'Adventure Works Corp. Toutefois, pour pouvoir effectuer cette leçon, vous devez ajouter une table qui contient les utilisateurs de votre propre domaine. Vous n'aurez pas besoin de mots de passe pour les noms d'utilisateurs qui seront ajoutés. Pour créer une table EmployeeSecurity, avec un petit groupe d’utilisateurs de votre propre domaine, vous allez utiliser la fonctionnalité Coller, le collage des données d’employé à partir d’une feuille de calcul Excel. Dans la réalité, la table contenant les noms d'utilisateurs à ajouter à un modèle utiliserait une table provenant d'une base de données actuelle comme source de données (une table dimEmployee réelle, par exemple).  
  
Pour implémenter la sécurité dynamique, vous allez utiliser deux nouvelles fonctions DAX : [Fonction USERNAME (DAX)](/dax/username-function-dax) et [LOOKUPVALUE, fonction (DAX)](/dax/lookupvalue-function-dax). Ces fonctions, appliquées dans une formule de filtre de lignes, sont définies dans un nouveau rôle. À l’aide de la fonction LOOKUPVALUE, la formule spécifie une valeur à partir de la table EmployeeSecurity, puis passe cette valeur à la fonction USERNAME, qui spécifie le nom d’utilisateur de l’utilisateur connecté appartient à ce rôle. L’utilisateur peut alors parcourir uniquement les données spécifiées par les filtres de lignes du rôle. Dans ce scénario, vous allez spécifier que les commerciaux peuvent uniquement parcourir les données de ventes Internet pour les secteurs de vente dont ils sont membres.  
  
Pour pouvoir effectuer cette leçon supplémentaire, vous allez accomplir une succession de tâches. Les tâches qui sont propres à ce scénario de modèle tabulaire Adventure Works, et qui ne s'appliqueraient pas forcément à un scénario réel, sont identifiées en conséquence. Chaque tâche inclut des informations supplémentaires qui en décrivent l'objectif.  
  
Durée estimée pour effectuer cette leçon : **30 minutes**  
  
## <a name="prerequisites"></a>Prérequis  
Cette leçon supplémentaire fait partie d’un didacticiel de modélisation tabulaire, qui doit être suivi dans l’ordre. Avant d'effectuer les tâches de cette leçon supplémentaire, vous devez avoir terminé toutes les leçons précédentes.  
  
## <a name="add-the-dimsalesterritory-table-to-the-aw-internet-sales-tabular-model-project"></a>Ajoutez la table dimSalesTerritory au projet Modèle tabulaire AW Internet Sales.  
Pour implémenter la sécurité dynamique pour ce scénario Adventure Works, vous devez ajouter deux tables supplémentaires à votre modèle. DimSalesTerritory est la première table à ajouter (sous le nom Sales Territory) à partir de la même base de données AdventureWorksDW. Plus tard, vous appliquerez un filtre de lignes à la table SalesTerritory qui définit les données spécifiques de l’utilisateur connecté peut parcourir.  
  
#### <a name="to-add-the-dimsalesterritory-table"></a>Pour ajouter la table dimSalesTerritory :  
  
1.  Dans SSDT, cliquez sur le **modèle** menu, puis sur **connexions existantes**.  
  
2.  Dans la boîte de dialogue **Connexions existantes** , vérifiez que la connexion à la source de données **Adventure Works DB from SQL** est sélectionnée, puis cliquez sur **Ouvrir**.  
  
    Si la boîte de dialogue informations d’identification d’emprunt d’identité s’affiche, tapez les informations d’identification d’emprunt d’identité que vous avez utilisé dans la leçon 2 : Ajouter des données.  
  
3.  Dans la page **Choisir comment importer les données** , laissez **Sélectionner les données à importer dans une liste de tables et de vues** sélectionné, puis cliquez sur **Suivant**.  
  
4.  Dans la page **Sélectionner des tables et des vues** , sélectionnez la table **DimSalesTerritory** .  
  
5.  Cliquez sur **Afficher un aperçu et filtrer**.  
  
6.  Désélectionnez la colonne **SalesTerritoryAlternateKey** , puis cliquez sur **OK**.  
  
7.  Dans la page **Sélectionner des tables et des vues** , cliquez sur **Terminer**.  
  
    La nouvelle table est ajoutée à l'espace de travail de modèle. Objets et données de la table DimSalesTerritory source sont ensuite importées dans votre modèle tabulaire AW Internet Sales.  
  
9. Une fois que la table a été importée, cliquez sur **Fermer**.  

## <a name="add-a-table-with-user-name-data"></a>Ajouter une table avec les noms d'utilisateur  
La table dimEmployee de l'exemple de base de données AdventureWorksDW contient des utilisateurs du domaine AdventureWorks, or ces noms d'utilisateurs n'existent pas dans votre propre environnement, vous devez donc créer une table dans votre modèle qui contient un petit groupe (trois) d'utilisateurs réels de votre organisation. Vous devez ensuite ajouter ces utilisateurs en tant que membres au nouveau rôle. Vous n'avez pas besoin de mots de passe pour les exemples de noms d'utilisateurs, mais vous avez besoin de noms d'utilisateurs Windows réels de votre propre domaine.  
  
#### <a name="to-add-an-employeesecurity-table"></a>Pour ajouter une table EmployeeSecurity  
  
1.  Ouvrez Microsoft Excel, en créant une nouvelle feuille de calcul.  
  
2.  Copiez la table suivante (y compris la ligne d'en-tête), puis collez-la dans la feuille de calcul.  

    ```
      |EmployeeId|SalesTerritoryId|FirstName|LastName|LoginId|  
      |---------------|----------------------|--------------|-------------|------------|  
      |1|2|<user first name>|<user last name>|\<domain\username>|  
      |1|3|<user first name>|<user last name>|\<domain\username>|  
      |2|4|<user first name>|<user last name>|\<domain\username>|  
      |3|5|<user first name>|<user last name>|\<domain\username>|  
    ```

3.  Remplacez le prénom, le nom de famille et le domaine\nom d’utilisateur avec les noms et les ID de connexion des trois utilisateurs de votre organisation. Pour EmployeeId 1, placez le même utilisateur sur les deux premières lignes. Cela signifie que cet utilisateur appartient à plusieurs secteurs de vente. Laisser les champs EmployeeId et SalesTerritoryId tels quels.  
  
4.  Enregistrez la feuille de calcul en tant que **SampleEmployee**.  
  
5.  Dans la feuille de calcul, sélectionnez toutes les cellules avec les données d’employé, y compris les en-têtes, puis cliquez sur les données sélectionnées, puis cliquez sur **copie**.  
  
6.  Dans SSDT, cliquez sur le **modifier** menu, puis sur **coller**.  
  
    Si coller est grisée, cliquez sur n’importe quelle colonne dans n’importe quelle table dans la fenêtre Concepteur de modèles, puis réessayez.  
  
7.  Dans le **Aperçu avant collage** boîte de dialogue **nom de la Table**, type **EmployeeSecurity**.  
  
8.  Dans **données à coller**, vérifiez que les données contiennent toutes des données utilisateur et des en-têtes à partir de la feuille de calcul SampleEmployee.  
  
9. Vérifiez que la case **Utiliser la première ligne comme en-têtes de colonnes** est cochée, puis cliquez sur **OK**.  
  
    Une nouvelle table nommée EmployeeSecurity les données des employés copiées à partir de la feuille de calcul SampleEmployee est créée.  
  
## <a name="create-relationships-between-factinternetsales-dimgeography-and-dimsalesterritory-table"></a>Créer des relations entre la table FactInternetSales, DimGeography et DimSalesTerritory  
La table FactInternetSales, DimGeography et DimSalesTerritory tous contenir une colonne commune, SalesTerritoryId. La colonne SalesTerritoryId de la table DimSalesTerritory contient des valeurs avec un Id différent pour chaque secteur de vente.  
  
#### <a name="to-create-relationships-between-the-factinternetsales-dimgeography-and-the-dimsalesterritory-table"></a>Pour créer des relations entre les FactInternetSales, DimGeography et dimsalesterritory  
  
1.  Dans le Générateur de modèles, dans la vue de diagramme, dans le **DimGeography** table, cliquez et maintenez le **SalesTerritoryId** colonne, puis faites glisser le curseur vers le **SalesTerritoryId** colonne dans la **DimSalesTerritory** table et relâchez.  
  
2.  Dans le **FactInternetSales** table, cliquez et maintenez le **SalesTerritoryId** colonne, puis faites glisser le curseur vers le **SalesTerritoryId** colonne dans la  **DimSalesTerritory** de table et relâchez.  
  
    Notez que la propriété Active pour cette relation est False, ce qui signifie qu’il est inactif. Il s’agit, car la table FactInternetSales a déjà une autre relation active qui est utilisée dans les mesures.  
  
## <a name="hide-the-employeesecurity-table-from-client-applications"></a>Masquer la EmployeeSecurity Table à partir d’applications clientes  
Dans cette tâche, vous allez masquer la table EmployeeSecurity, empêchant de s’afficher dans la liste de champs d’une application cliente. Gardez bien à l'esprit que le fait de masquer une table ne la sécurise pas. Les utilisateurs peuvent toujours interroger les données de la table EmployeeSecurity s’ils savent comment. Afin de sécuriser les données de table EmployeeSecurity en empêchant les utilisateurs d’interroger n’importe laquelle de ses données, vous allez appliquer un filtre dans une tâche ultérieure.  
  
#### <a name="to-hide-the-employeesecurity-table-from-client-applications"></a>Pour masquer la table EmployeeSecurity à partir d’applications clientes  
  
-   Dans le Générateur de modèles, dans la Vue de diagramme, cliquez avec le bouton droit sur l’en-tête de la table **Employee** puis sur **Masquer dans les outils clients**.  
  
## <a name="create-a-sales-employees-by-territory-user-role"></a>Créer un rôle d'utilisateur Sales Employees by Territory  
Dans cette tâche, vous allez créer un rôle d'utilisateur. Ce rôle inclut un filtre de lignes définissant les lignes de la table DimSalesTerritory sont visibles aux utilisateurs. Le filtre est ensuite appliqué dans la direction de la relation un-à-plusieurs à toutes les autres tables associées à DimSalesTerritory. Vous allez également appliquer un filtre simple qui sécurise la table EmployeeSecurity entière d’être interrogée par tout utilisateur qui est membre du rôle.  
  
> [!NOTE]  
> Le rôle Sales Employees by Territory que vous créez dans cette leçon autorise les membres à parcourir (ou à interroger) uniquement les données de ventes pour le secteur de vente auquel ils appartiennent. Si vous ajoutez un utilisateur en tant que membre pour les employés des ventes par rôle Territory qui existe également comme un membre d’un rôle créé dans [leçon 11 : Créer des rôles](lesson-11-create-roles.md), vous obtiendrez une combinaison d’autorisations. Lorsqu'un utilisateur est membre de plusieurs rôles, les autorisations et les filtres de lignes définis pour chaque rôle se cumulent. Autrement dit, l'utilisateur aura plus d'autorisations déterminées par la combinaison des rôles.  
  
#### <a name="to-create-a-sales-employees-by-territory-user-role"></a>Pour créer un rôle d'utilisateur Sales Employees by Territory  
  
1.  Dans SSDT, cliquez sur le **modèle** menu, puis sur **rôles**.  
  
2.  Dans **Gestionnaire de rôles**, cliquez sur **New**.  
  
    Un nouveau rôle sans aucune autorisation est ajouté à la liste.  
  
3.  Cliquez sur le nouveau rôle puis, dans la colonne **Nom** , renommez le rôle en **Sales Employees by Territory**.  
  
4.  Dans la colonne **Autorisations**, cliquez sur la liste déroulante, puis sélectionnez l’autorisation **Lecture**.  
  
5.  Cliquez sur l’onglet **Membres** , puis cliquez sur **Ajouter**.  
  
6.  Dans le **sélectionner utilisateur ou groupe** boîte de dialogue **entrer l’objet à sélectionner**, tapez le nom d’utilisateur premier exemple vous avez utilisé lors de la création de la table EmployeeSecurity. Cliquez sur **Vérifier les noms** pour vérifier que le nom d’utilisateur est valide, puis cliquez sur **OK**.  
  
    Répétez cette étape, en ajoutant les autres noms d’utilisateur exemple que vous avez utilisé lors de la création de la table EmployeeSecurity.  
  
7.  Cliquez sur l’onglet **Filtres de lignes** .  
  
8.  Pour le **EmployeeSecurity** de table, dans le **filtre DAX** colonne, tapez la formule suivante.  
  
    ```
      =FALSE()  
    ```
  
    Cette formule indique que toutes les colonnes se résolvent en condition booléenne ; false Par conséquent, aucune colonne de la table employeesecurity ne peut être interrogée par un membre des employés de ventes par rôle d’utilisateur territoire.  
  
9. Pour la table **DimSalesTerritory** .  

    ```  
    ='Sales Territory'[Sales Territory Id]=LOOKUPVALUE('Employee Security'[Sales Territory Id], 
      'Employee Security'[Login Id], USERNAME(), 
      'Employee Security'[Sales Territory Id], 
      'Sales Territory'[Sales Territory Id]) 
    ```
  
    Dans cette formule, la fonction LOOKUPVALUE retourne toutes les valeurs pour la colonne DimEmployeeSecurity [SalesTerritoryId], où la valeur EmployeeSecurity [LoginId] est le même que l’actuellement connecté sur le nom d’utilisateur Windows et EmployeeSecurity [SalesTerritoryId] est le identique à la valeur DimSalesTerritory [SalesTerritoryId].  
  
    L’ensemble du secteur de vente ID retournés par LOOKUPVALUE est ensuite utilisé pour limiter les lignes affichées dans la table DimSalesTerritory. Seules les lignes où la valeur SalesTerritoryID de la ligne est dans le jeu d’ID retournée par la fonction LOOKUPVALUE sont affichées.  
  
10. Dans le Gestionnaire de rôles, cliquez sur **Ok**.  
  
## <a name="test-the-sales-employees-by-territory-user-role"></a>Tester le rôle Sales Employees by Territory User  
Dans cette tâche, vous utiliserez l’analyser dans la fonctionnalité d’Excel dans SSDT pour tester l’efficacité des employés de ventes par rôle d’utilisateur territoire. Vous allez spécifier l’un des noms d’utilisateurs que vous avez ajouté à la table EmployeeSecurity et en tant que membre du rôle. Ce nom d'utilisateur sera ensuite utilisé comme le nom d'utilisateur effectif dans la connexion créée entre Excel et le modèle.  
  
#### <a name="to-test-the-sales-employees-by-territory-user-role"></a>Pour tester le rôle d'utilisateur Sales Employees by Territory  
  
1.  Dans SSDT, cliquez sur le **modèle** menu, puis sur **analyser dans Excel**.  
  
2.  Dans la boîte de dialogue **Analyser dans Excel** , dans **Spécifier le nom d’utilisateur ou le rôle à utiliser pour se connecter au modèle**, sélectionnez **Autre utilisateur Windows**, puis cliquez sur **Parcourir**.  
  
3.  Dans le **sélectionner utilisateur ou groupe** boîte de dialogue **Entrez le nom de l’objet à sélectionner**, tapez un des noms d’utilisateur que vous avez inclus dans la table EmployeeSecurity, puis cliquez sur **vérifier les noms**.  
  
4.  Cliquez sur **OK** pour fermer la boîte de dialogue **Sélectionner l’utilisateur ou le groupe** , puis cliquez à nouveau sur **OK** pour fermer la boîte de dialogue **Analyser dans Excel** .  
  
    Excel s'ouvre avec un nouveau classeur. Un tableau croisé dynamique est automatiquement créé. La liste PivotTable Fields inclut la plupart des champs de données disponibles dans votre nouveau modèle.  
  
    Notez que la table EmployeeSecurity n’est pas visible dans la liste PivotTable Fields. Cela est dû au fait que vous avez choisi de masquer cette table des outils clients dans une tâche précédente.  
  
5.  Dans le **champs** liste dans **∑ Internet Sales** (mesures), sélectionnez le **InternetTotalSales** mesure. La mesure sera ensuite entrée dans les champs **Valeurs** .  
  
6.  Sélectionnez le **SalesTerritoryId** colonne à partir de la **DimSalesTerritory** table. La colonne est ensuite entrée dans les champs **Étiquettes de ligne** .  
  
    Notez que les chiffres de ventes sur Internet s'affichent uniquement pour le secteur auquel appartient le nom d'utilisateur que vous avez utilisé. Si vous sélectionnez une autre colonne ; par exemple, City, dans la table DimGeography comme champ d’étiquette de ligne, seules les villes du secteur de vente auquel appartient l’utilisateur effectif sont affichées.  
  
    Cet utilisateur ne peut pas parcourir ou interroger les données des ventes Internet pour les secteurs autres que celui auquel il appartient, car le filtre de lignes défini pour la table Sales Territory dans le rôle d'utilisateur Sales Employees by Territory sécurise efficacement toutes les données associées à d'autres secteurs de vente.  
  
## <a name="see-also"></a>Voir aussi  
[fonction USERNAME (DAX)](/dax/username-function-dax)  
[fonction LOOKUPVALUE (DAX)](/dax/lookupvalue-function-dax)  
[Fonction CUSTOMDATA (DAX)](/dax/customdata-function-dax)  
