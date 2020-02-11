---
title: Implémenter la sécurité dynamique à l’aide de filtres de lignes | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8bf03c45-caf5-4eda-9314-e4f8f24a159f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 39d0d92d83a41970dcddae54d74aca3d118dcf6f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "69530878"
---
# <a name="implement-dynamic-security-by-using-row-filters"></a>Implémentation de la sécurité dynamique à l'aide des filtres de lignes
  Dans cette leçon supplémentaire, vous allez créer un rôle supplémentaire qui implémente la sécurité dynamique. La sécurité dynamique offre une sécurité au niveau des lignes basée sur le nom ou sur l’ID de connexion de l’utilisateur actuellement connecté. Pour plus d’informations, consultez [Rôles &#40;SSAS Tabulaire&#41;](https://docs.microsoft.com/analysis-services/tabular-models/roles-ssas-tabular).  
  
 Pour implémenter la sécurité dynamique, vous devez ajouter une table à votre modèle qui contient les noms des utilisateurs Windows qui peuvent créer une connexion au modèle comme source de données et parcourir les objets de modèle et les données. Le modèle que vous allez créer à l'aide de ce didacticiel est dans le contexte d'Adventure Works Corp. Toutefois, pour pouvoir effectuer cette leçon, vous devez ajouter une table qui contient les utilisateurs de votre propre domaine. Vous n'aurez pas besoin de mots de passe pour les noms d'utilisateurs qui seront ajoutés. Pour créer une table Employee Security contenant un petit groupe d'utilisateurs de votre propre domaine, vous allez utiliser la fonctionnalité Coller pour coller les données à propos des employés à partir d'une feuille de calcul Excel. Dans la réalité, la table contenant les noms d'utilisateurs à ajouter à un modèle utiliserait une table provenant d'une base de données actuelle comme source de données (une table dimEmployee réelle, par exemple).  
  
 Pour implémenter la sécurité dynamique, vous allez utiliser deux nouvelles fonctions DAX : la [fonction USERNAME &#40;la fonction dax&#41;](/dax/username-function-dax) et [VALRECH &#40;&#41;Dax ](/dax/lookupvalue-function-dax). Ces fonctions, appliquées dans une formule de filtre de lignes, sont définies dans un nouveau rôle. Si vous utilisez la fonction LOOKUPVALUE, la formule spécifie une valeur à partir de la table Employee Security et la transmet ensuite à la fonction USERNAME, qui spécifie le nom d'utilisateur de l'utilisateur connecté à qui appartient ce rôle. L’utilisateur peut ensuite parcourir uniquement les données spécifiées par les filtres de lignes du rôle. Dans ce scénario, vous allez spécifier que les commerciaux peuvent uniquement parcourir les données de ventes Internet pour les secteurs de vente dont ils sont membres.  
  
 Pour pouvoir effectuer cette leçon supplémentaire, vous allez accomplir une succession de tâches. Les tâches qui sont propres à ce scénario de modèle tabulaire Adventure Works, mais qui ne s’appliqueraient pas nécessairement dans la vraie vie, sont identifiées comme telles. Chaque tâche inclut des informations supplémentaires décrivant son objectif.  
  
 Durée estimée pour effectuer cette leçon : **30 minutes**  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Cette rubrique de leçon supplémentaire fait partie d’un didacticiel de modélisation tabulaire, qui doit être suivi dans l’ordre prévu. Avant d’effectuer les tâches de cette leçon supplémentaire, vous devez avoir suivi toutes les leçons précédentes.  
  
## <a name="add-the-dimsalesterritory-table-to-the-aw-internet-sales-tabular-model-project"></a>Ajoutez la table dimSalesTerritory au projet Modèle tabulaire AW Internet Sales.  
 Pour implémenter la sécurité dynamique pour ce scénario Adventure Works, vous devez ajouter deux tables supplémentaires à votre modèle. DimSalesTerritory est la première table à ajouter (sous le nom Sales Territory) à partir de la même base de données AdventureWorksDW. Vous devez ensuite appliquer un filtre de lignes à la table Sales Territory qui définit les données spécifiques que l'utilisateur connecté peut parcourir.  
  
#### <a name="to-add-the-dimsalesterritory-table"></a>Pour ajouter la table dimSalesTerritory :  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis sur **Connexions existantes**.  
  
2.  Dans la boîte de dialogue **Connexions existantes** , vérifiez que la connexion à la source de données **Adventure Works DB from SQL** est sélectionnée, puis cliquez sur **Ouvrir**.  
  
     Si la boîte de dialogue Informations d’identification s’affiche, tapez les informations d’emprunt d’identification que vous avez utilisé dans la leçon 2 : Ajouter des données.  
  
3.  Dans la page **Choisir comment importer les données** , laissez **Sélectionner les données à importer dans une liste de tables et de vues** sélectionné, puis cliquez sur **Suivant**.  
  
4.  Dans la page **Sélectionner des tables et des vues** , sélectionnez la table **DimSalesTerritory** .  
  
5.  Dans la colonne Nom convivial, tapez **Sales Territory**.  
  
6.  Cliquez sur **Afficher un aperçu et filtrer**.  
  
7.  Désélectionnez la colonne **SalesTerritoryAlternateKey** , puis cliquez sur **OK**.  
  
8.  Dans la page **Sélectionner des tables et des vues** , cliquez sur **Terminer**.  
  
     La nouvelle table est ajoutée à l'espace de travail de modèle. Les objets et les données de la table dimSalesTerritory source sont ensuite importés dans la nouvelle table Sales Territory dans votre Modèle tabulaire AW Internet Sales.  
  
9. Une fois que la table a été importée, cliquez sur **Fermer**.  
  
## <a name="give-the-columns-friendly-names"></a>Attribuer des noms conviviaux aux colonnes  
 Dans cette tâche, vous allez renommer les colonnes dans la table Sales Territory et leur donner des noms conviviaux. Il n'est pas nécessaire de donner systématiquement aux tables et/ou aux colonnes des noms conviviaux ; toutefois, cela facilite la navigation dans votre projet à partir du Concepteur de modèles et le repérage par les utilisateurs des objets de modèle et des données dans une liste, dans une application cliente.  
  
#### <a name="to-rename-columns-in-the-sales-territory-table"></a>Pour renommer des colonnes de la table Sales Territory :  
  
-   Dans le concepteur de modèles, renommez les colonnes de la table **Sales Territory** :  
  
     **Sales Territory**  
  
    |Nom de la source|Nom convivial|  
    |-----------------|-------------------|  
    |SalesTerritoryKey|Sales Territory Id|  
    |SalesTerritoryRegion|Sales Territory Region|  
    |SalesTerritoryCountry|Sales Territory Country|  
    |SalesTerritoryGroup|Sales Territory Group|  
  
## <a name="add-a-table-with-user-name-data"></a>Ajouter une table avec des données de noms d’utilisateur  
 La table dimEmployee de l'exemple de base de données AdventureWorksDW contient des utilisateurs du domaine AdventureWorks, or ces noms d'utilisateurs n'existent pas dans votre propre environnement, vous devez donc créer une table dans votre modèle qui contient un petit groupe (trois) d'utilisateurs réels de votre organisation. Vous devez ensuite ajouter ces utilisateurs en tant que membres au nouveau rôle. Vous n'avez pas besoin de mots de passe pour les exemples de noms d'utilisateurs, mais vous avez besoin de noms d'utilisateurs Windows réels de votre propre domaine.  
  
#### <a name="to-add-an-employee-security-table"></a>Pour ajouter une table Employee Security :  
  
1.  Ouvrez Microsoft Excel, ce qui crée une feuille de calcul.  
  
2.  Copiez la table suivante, notamment la ligne d’en-tête, puis collez-la dans la feuille de calcul.  
  
    |Employee Id|Sales Territory Id|Prénom|Nom|Login Id|  
    |-----------------|------------------------|----------------|---------------|--------------|  
    |1|2|\<prénom de l’utilisateur>|\<nom de l’utilisateur>|\<> domaine\nom_utilisateur|  
    |1|3|\<prénom de l’utilisateur>|\<nom de l’utilisateur>|\<> domaine\nom_utilisateur|  
    |2|4|\<prénom de l’utilisateur>|\<nom de l’utilisateur>|\<> domaine\nom_utilisateur|  
    |3|5|\<prénom de l’utilisateur>|\<nom de l’utilisateur>|\<> domaine\nom_utilisateur|  
  
3.  Dans la nouvelle feuille de calcul, remplacez le prénom, le nom, et le domaine\nom d'utilisateur par les noms et les ID de connexion des trois utilisateurs de votre organisation. Pour l'ID d'employé 1, indiquez le même utilisateur sur les deux premières lignes. Cela signifie que cet utilisateur appartient à plusieurs secteurs de vente. Laissez les champs Employee Id et Sales Territory Id tels quels.  
  
4.  Enregistrez la feuille de `Sample Employee`calcul sous.  
  
5.  Dans la feuille de calcul, sélectionnez toutes les cellules avec des données sur les employés, avec les en-têtes, puis cliquez avec le bouton droit sur les données sélectionnées, et cliquez ensuite sur **Copier**.  
  
6.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modifier**, puis sur **Coller**.  
  
     Si l’option Coller est grisée, cliquez sur n’importe quelle colonne dans une table de la fenêtre du Générateur de modèles, cliquez ensuite sur le menu **Modifier**, puis sur **Coller**.  
  
7.  Dans la boîte de dialogue **aperçu de collage** , dans nom de `Employee Security`la **table**, tapez.  
  
8.  Dans **Données à coller**, vérifiez que les données contiennent toutes les données et en-têtes d’utilisateur de la feuille de calcul Sample Employee.  
  
9. Vérifiez que la case **Utiliser la première ligne comme en-têtes de colonne** est cochée, puis cliquez sur **OK**.  
  
     Une table nommée Employee Security avec les données sur les employés copiées à partir de la feuille de calcul Sample Employee est créée.  
  
## <a name="create-relationships-between-internet-sales-geography-and-sales-territory-table"></a>Créer des relations entre les tables Internet Sales, Geography et Sales Territory  
 Les tables Internet Sales, Geography et sales secteur contiennent toutes une colonne commune, ID de secteur de vente. La colonne ID du secteur de vente de la table secteur de vente contient des valeurs avec un ID différent pour chaque secteur de vente.  
  
#### <a name="to-create-relationships-between-the-internet-sales-geography-and-the-sales-territory-table"></a>Pour créer des relations entre les tables lnternet Sales, Geography et Sales Territory  
  
1.  Dans le Générateur de modèles, dans la Vue de diagramme, dans la table **Geography**, cliquez et maintenez la sélection de la colonne **Sales Territory Id**, faites ensuite glisser le curseur sur la colonne **Sales Territory Id** dans la table **Sales Territory**, et relâchez la souris.  
  
2.  Dans la table **Internet Sales**, cliquez et maintenez la sélection de la colonne **Sales Territory Id**, faites glisser le curseur sur la colonne **Sales Territory Id** dans la table **Sales Territory**, et relâchez la souris.  
  
     Notez que la propriété Active pour cette relation est False, ce qui signifie qu'elle est inactive. Cela est dû au fait que la table Internet Sales a déjà une autre relation active qui est utilisée dans les mesures.  
  
## <a name="hide-the-employee-security-table-from-client-applications"></a>Masquer la table Employee Security des applications clientes  
 Dans cette tâche, vous allez masquer la table Employee Security, afin qu’elle apparaisse dans la liste des champs d’une application cliente. N’oubliez pas que masquer une table ne garantit pas sa sécurité. Les utilisateurs peuvent toujours interroger les données de la table Employee Security s'ils savent comment faire. Afin de sécuriser les données de la table Employee Security, pour empêcher les utilisateurs d'interroger n'importe laquelle de ses données, vous devez appliquer un filtre dans une tâche ultérieure.  
  
#### <a name="to-hide-the-employee-table-from-client-applications"></a>Pour masquer la table Employee Security des applications clientes  
  
-   Dans le Concepteur de modèles, dans la vue de diagramme, cliquez sur l’en-tête de la table **Employee**, puis cliquez sur **Masquer dans les outils clients**.  
  
## <a name="create-a-sales-employees-by-territory-user-role"></a>Créer un rôle d’utilisateur Sales Employees by Territory (Représentants commerciaux par secteur)  
 Dans cette tâche, vous allez créer un rôle d'utilisateur. Ce rôle inclut une définition de filtre de lignes dont les lignes de la table Sales Territory sont visibles aux utilisateurs. Le filtre est ensuite appliqué dans la direction de la relation un-à-plusieurs à toutes les autres tables associées à la table Sales Territory. Vous allez également appliquer un filtre simple qui empêche la table Employee Security d'être interrogée par tout utilisateur membre du rôle.  
  
> [!NOTE]  
>  Le rôle Sales Employees by Territory (Représentants commerciaux par secteur) que vous créez dans cette leçon limite les membres à parcourir (ou à interroger) uniquement les données des ventes pour le secteur de vente auquel ils appartiennent. Si vous ajoutez un utilisateur comme membre au rôle Sales Employees by Territory et qu’il est également membre d’un rôle créé dans la [Leçon 12 : Créer des rôles](../analysis-services/lesson-11-create-roles.md), vous obtiendrez une combinaison des autorisations. Quand un utilisateur est membre de plusieurs rôles, les autorisations et les filtres de lignes définis pour chaque rôle sont cumulatifs. Autrement dit, l'utilisateur aura plus d'autorisations déterminées par la combinaison des rôles.  
  
#### <a name="to-create-a-sales-employees-by-territory-user-role"></a>Pour créer un rôle d’utilisateur Sales Employees by Territory (Représentants commerciaux par secteur)  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle**, puis sur **Rôles**.  
  
2.  Dans la boîte de dialogue **Gestionnaire de rôles** , cliquez sur **Nouveau**.  
  
     Un nouveau rôle avec l’autorisation Aucune est ajouté à la liste.  
  
3.  Cliquez sur le nouveau rôle, puis dans la colonne **nom** , renommez le rôle `Sales Employees by Territory`.  
  
4.  Dans la colonne **Autorisations**, cliquez sur la liste déroulante et sélectionnez l’autorisation **Lecture**.  
  
5.  Cliquez sur l’onglet **Membres** , puis cliquez sur **Ajouter**.  
  
6.  Dans la boîte de dialogue **Sélectionner l’utilisateur ou le groupe**, dans **Entrez le nom de l’objet à sélectionner**, tapez le premier exemple de nom d’utilisateur que vous avez utilisé lors de la création la table Employee Security. Cliquez sur **Vérifier les noms** pour vérifier si le nom d’utilisateur est valide, puis cliquez sur **OK**.  
  
     Répétez cette étape et ajoutez les autres exemples de noms d'utilisateurs que vous avez utilisés lors de la création de la table Employee Security.  
  
7.  Cliquez sur l’onglet **Filtres de lignes**.  
  
8.  Pour la `Employee Security` table, dans la colonne **filtre Dax** , tapez la formule suivante.  
  
     `=FALSE()`  
  
     Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE pour l'accepter.  
  
     Cette formule indique que toutes les colonnes résolvent à la condition booléenne false ; par conséquent, aucune colonne de la table Employee Security ne peut être interrogée par un membre du rôle d'utilisateur Sales Employees by Territory.  
  
9. Tapez la formule suivante pour la table **Sales Territory**.  
  
     `='Sales Territory'[Sales Territory Id]=LOOKUPVALUE('Employee Security'[Sales Territory Id], 'Employee Security'[Login Id], USERNAME(), 'Employee Security'[Sales Territory Id], 'Sales Territory'[Sales Territory Id])`  
  
     Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE pour l'accepter.  
  
     Dans cette formule, la fonction LOOKUPVALUE retourne toutes les valeurs pour la colonne Employee Security[Sales Territory Id], où Employee Security[Login Id] est le même que le nom d'utilisateur Windows actuellement connecté, et Employee Security[Sales Territory Id] est le même que Sales Territory[Sales Territory Id].  
  
     L'ensemble des identifiants Sales Territory ID retournés par LOOKUPVALUE est ensuite utilisé pour limiter le nombre de lignes affichées dans la table Sales Territory. Seules les lignes dont l'identifiant Sales Territory ID figure dans l'ensemble d'identifiants retournés par la fonction LOOKUPVALUE sont affichées.  
  
10. Dans la boîte de dialogue Gestionnaire de rôles, cliquez sur **OK**.  
  
## <a name="test-the-sales-employees-by-territory-user-role"></a>Tester le rôle d’utilisateur Sales Employees by Territory (Représentants commerciaux par secteur)  
 Dans cette tâche, vous allez utiliser la fonctionnalité Analyser dans Excel dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] pour tester l'efficacité du rôle d'utilisateur Sales Employees by Territory. Vous allez spécifier l'un des noms d'utilisateurs que vous avez ajoutés à la table Employee Security et en tant que membre du rôle. Ce nom d'utilisateur sera ensuite utilisé comme le nom d'utilisateur effectif dans la connexion créée entre Excel et le modèle.  
  
#### <a name="to-test-the-sales-employees-by-territory-user-role"></a>Pour tester le rôle d’utilisateur Sales Employees by Territory (Représentants commerciaux par secteur)  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis sur **Analyser dans Excel**.  
  
2.  Dans la boîte de dialogue **Analyser dans Excel**, dans **Spécifier le nom d’utilisateur ou le rôle à utiliser pour se connecter au modèle**, sélectionnez **Autre utilisateur Windows**, puis cliquez sur **Parcourir**.  
  
3.  Dans la boîte de dialogue **Sélectionner l’utilisateur ou le groupe**, dans **Entrez le nom de l’objet à sélectionner**, tapez un des noms d’utilisateurs que vous avez inclus dans la table Employee, puis cliquez sur **Vérifier les noms**.  
  
4.  Cliquez sur **OK** pour fermer la boîte de dialogue **Sélectionner un utilisateur ou un groupe**, puis cliquez sur **OK** pour fermer la boîte de dialogue **Analyser dans Excel**.  
  
     Excel s’ouvre avec un nouveau classeur. Un tableau croisé dynamique est créé automatiquement. La liste des champs du tableau croisé dynamique inclut la plupart des champs de données disponibles dans votre nouveau modèle.  
  
     Notez que la table Employee Security n'est pas visible dans la liste de champs du tableau croisé dynamique. Cela est dû au fait que vous avez choisi de masquer cette table des outils clients dans une tâche précédente.  
  
5.  Dans la liste **Champ de tableau croisé dynamique**, dans **∑ Internet Sales** (mesures), sélectionnez la mesure **Internet Total Sales**. La mesure sera ensuite entrée dans les champs **Valeurs** .  
  
6.  Dans la zone **Champ de tableau croisé dynamique**, sélectionnez la colonne **Sales Territory Id** à partir de la table **Sales Territory**. La colonne est ensuite entrée dans les champs **Étiquettes de ligne** .  
  
     Notez que les chiffres des ventes sur Internet s’affichent uniquement pour la région à laquelle le nom d’utilisateur effectif que vous avez utilisé appartient. Si vous sélectionnez une autre colonne (City, par exemple) dans la table Geography en tant que champ d'étiquette de ligne, seules les villes du secteur de vente auquel appartient l'utilisateur sont affichées.  
  
     Cet utilisateur ne peut pas parcourir ou interroger les données des ventes Internet pour les secteurs autres que celui auquel il appartient, car le filtre de lignes défini pour la table Sales Territory dans le rôle d'utilisateur Sales Employees by Territory sécurise efficacement toutes les données associées à d'autres secteurs de vente.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction USERNAME &#40;&#41;DAX](/dax/username-function-dax)   
 [Fonction VALRECH &#40;&#41;DAX](/dax/lookupvalue-function-dax)   
 [Fonction CUSTOMDATA &#40;&#41;DAX](/dax/customdata-function-dax)  
  
  
