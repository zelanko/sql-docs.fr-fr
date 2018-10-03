---
title: Clause COMPUTE de forme | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- compute clause [ADO]
- data shaping [ADO], COMPUTE clause
ms.assetid: 3fdfead2-b5ab-4163-9b1d-3d2143a5db8c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f47c18d4bef6930d45ceb8e2c7ebf3bfabb86640
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47797873"
---
# <a name="shape-compute-clause"></a>Clause COMPUTE de la commande SHAPE
Une clause COMPUTE de forme génère un parent **Recordset**, dont les colonnes sont constituées d’une référence à l’enfant **Recordset**; facultatif dont le contenu est chapitre, nouveau, ou des colonnes calculées, des colonnes ou le résultat de l’exécution des fonctions d’agrégation sur l’enfant **Recordset** précédemment finies ou **Recordset**; et toutes les colonnes à partir de l’enfant **Recordset** répertoriées dans facultatif par clause.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SHAPE child-command [AS] child-alias  
   COMPUTE child-alias [[AS] name], [appended-column-list]  
   [BY grp-field-list]  
```  
  
## <a name="description"></a>Description  
 Les parties de cette clause sont les suivantes :  
  
 *commande enfant*  
 Se compose d’une des opérations suivantes :  
  
-   Une commande de requête entre accolades («{}») qui retourne un enfant **Recordset** objet. La commande est émise au fournisseur de données sous-jacent et sa syntaxe dépend de la configuration requise de ce fournisseur. Ce sera généralement le langage SQL, bien qu’ADO ne nécessite pas de n’importe quel langage de requête spécifique.  
  
-   Le nom d’un existant en forme **Recordset**.  
  
-   Une autre commande de forme.  
  
-   Le mot-clé TABLE, suivi du nom d’une table dans le fournisseur de données.  
  
 *alias-enfant*  
 Alias utilisé pour faire référence à la **Recordset** retourné par la *commande enfant.* Le *enfant-alias* est requis dans la liste des colonnes dans la clause COMPUTE et définit la relation entre parent et enfant **Recordset** objets.  
  
 *appended-column-list*  
 Une liste dans laquelle chaque élément définit une colonne dans le parent généré. Chaque élément contient une colonne de chapitre, une nouvelle colonne, une colonne calculée ou une valeur obtenue à partir d’une fonction d’agrégation sur l’enfant **Recordset**.  
  
 *grp-field-list*  
 Une liste de colonnes dans le parent et enfant **Recordset** objets qui spécifie la façon dont les lignes doivent être groupées dans l’enfant.  
  
 Pour chaque colonne dans le *grp-field-list,* il existe une colonne correspondante dans l’enfant et parent **Recordset** objets. Pour chaque ligne de la page parente **Recordset**, le *grp liste de champs* colonnes ont des valeurs uniques et l’enfant **Recordset** référencé par le parent ligne se compose uniquement d’enfant les lignes dont la propriété *liste de champs grp* colonnes ont les mêmes valeurs que la ligne parente.  
  
 Si la clause BY est incluse, l’enfant **Recordset**de lignes seront regroupées selon les colonnes dans la clause COMPUTE. Le parent **Recordset** contiendra une ligne pour chaque groupe de lignes de l’enfant **Recordset**.  
  
 Si la clause BY est omise, l’intégralité de l’enfant **Recordset** est traité comme un seul groupe et le parent **Recordset** contient exactement une ligne. Cette ligne fait référence à l’intégralité de l’enfant **Recordset**. L’omission de la clause BY vous permet de calculer des agrégats de « total général » tout l’enfant **Recordset**.  
  
 Exemple :  
  
```  
SHAPE {select * from Orders} AS orders             COMPUTE orders, SUM(orders.OrderAmount) as TotalSales         
```  
  
 Quel que soit le parent **Recordset** est formée (à l’aide de calcul ou APPEND), il contiendra une colonne de chapitre qui sert à associer à un enfant **Recordset**. Si vous le souhaitez, le parent **Recordset** peuvent également contenir des colonnes contenant des agrégats (SUM, MIN, MAX et ainsi de suite) sur les lignes enfants. Le parent et l’enfant **Recordset** peuvent contenir des colonnes qui contiennent une expression sur la ligne dans le **Recordset**, ainsi que les colonnes qui sont nouveaux et initialement vide.  
  
## <a name="operation"></a>Opération  
 Le *commande enfant* est émis pour le fournisseur, qui retourne un enfant **Recordset**.  
  
 La clause COMPUTE spécifie les colonnes du parent **Recordset**, qui peut être une référence à l’enfant **Recordset**, un ou plusieurs agrégats, d’une expression calculée ou de nouvelles colonnes. Si une clause BY est, les colonnes qu’elle définit sont également ajoutées au parent **Recordset**. La clause BY spécifie comment les lignes de l’enfant **Recordset** sont regroupés.  
  
 Par exemple, supposons que vous avez une table nommée des données démographiques, qui se compose de champs d’état, ville et remplissage. (Les chiffres dans la table sont fournis uniquement à un exemple).  
  
|État|Ville|Remplissage|  
|-----------|----------|----------------|  
|WA|Seattle|700,000|  
|- ou -|Medford|200,000|  
|- ou -|Portland|400,000|  
|CA|Los Angeles|800,000|  
|CA|San Diego|600,000|  
|WA|Tacoma|500,000|  
|- ou -|Corvallis|300,000|  
  
 Maintenant, exécutez cette commande de la forme :  
  
```  
rst.Open  "SHAPE {select * from demographics} AS rs "  & _  
          "COMPUTE rs, SUM(rs.population) BY state", _  
           objConnection  
```  
  
 Cette commande ouvre une forme **Recordset** à deux niveaux. Le niveau parent est un généré **Recordset** avec une colonne d’agrégation (`SUM(rs.population)`), une colonne faisant référence à l’enfant **Recordset** (`rs`) et une colonne pour le regroupement de l’enfant **Recordset** (`state`). Le niveau enfant est la **Recordset** retourné par la commande de requête (`select * from demographics`).  
  
 L’enfant **Recordset** lignes de détails seront regroupés par état, mais dans aucun ordre particulier. Autrement dit, les groupes ne seront pas dans l’ordre alphabétique ou numérique. Si vous souhaitez que le parent **Recordset** pour être triée, vous pouvez utiliser la **tri du jeu d’enregistrements** pour classer le parent **Recordset**.  
  
 Vous pouvez désormais parcourir le parent **Recordset** et accéder aux détails de l’enfant **Recordset** objets. Pour plus d’informations, consultez [accès aux lignes d’un Recordset hiérarchique](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md).  
  
## <a name="resultant-parent-and-child-detail-recordsets"></a>Parent résultant et jeux d’enregistrements de détail enfants  
  
### <a name="parent"></a>Parent  
  
|Somme (rs. Remplissage)|rs|État|  
|---------------------------|--------|-----------|  
|1,300,000|Référence à Enfant1|CA|  
|1,200,000|Référence à Enfant2|WA|  
|1,100,000|Référence à enfant 3|- ou -|  
  
## <a name="child1"></a>Enfant1  
  
|État|Ville|Remplissage|  
|-----------|----------|----------------|  
|CA|Los Angeles|800,000|  
|CA|San Diego|600,000|  
  
## <a name="child2"></a>Enfant2  
  
|État|Ville|Remplissage|  
|-----------|----------|----------------|  
|WA|Seattle|700,000|  
|WA|Tacoma|500,000|  
  
## <a name="child3"></a>Child3  
  
|État|Ville|Remplissage|  
|-----------|----------|----------------|  
|- ou -|Medford|200,000|  
|- ou -|Portland|400,000|  
|- ou -|Corvallis|300,000|  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux lignes dans un Recordset hiérarchique](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Vue d’ensemble de la mise en forme des données](../../../ado/guide/data/data-shaping-overview.md)   
 [Objet de champ](../../../ado/reference/ado-api/field-object.md)   
 [Grammaire de la mise en forme formelle](../../../ado/guide/data/formal-shape-grammar.md)   
 [Objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Fournisseurs requis pour la mise en forme des données](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Clause APPEND de forme](../../../ado/guide/data/shape-append-clause.md)   
 [En général, les commandes de forme](../../../ado/guide/data/shape-commands-in-general.md)   
 [Valeur de propriété (ADO)](../../../ado/reference/ado-api/value-property-ado.md)   
 [Fonctions Visual Basic pour Applications](../../../ado/guide/data/visual-basic-for-applications-functions.md)
