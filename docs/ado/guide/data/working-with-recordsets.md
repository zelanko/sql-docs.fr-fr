---
title: Utilisation des Recordsets | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset object [ADO]
ms.assetid: bdf9a56a-de4a-44de-9111-2f11ab7b16ea
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8e3c3c7ff7d623d3bec0adf60773266bb6e53571
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66704434"
---
# <a name="working-with-recordsets"></a>Utilisation des recordsets
Le **Recordset** objet dispose de fonctionnalités intégrées qui permettent de vous réorganiser l’ordre des données dans le jeu de résultats, pour rechercher un enregistrement spécifique en fonction de critères que vous fournissez et d’optimiser ces opérations de recherche à l’aide d’index. Si ces fonctionnalités sont disponibles pour une utilisation dépend du fournisseur et dans certains cas - tels que celui de la [Index](../../../ado/reference/ado-api/index-property.md) propriété - la structure de la source de données.  
  
## <a name="arranging-data"></a>Organisation des données  
 Souvent, le moyen le plus efficace pour trier les données dans votre **Recordset** consiste à spécifier une clause ORDER BY dans la commande SQL utilisée pour renvoyer des résultats. Toutefois, vous devrez peut-être modifier l’ordre des données dans un **Recordset** qui a déjà été créé. Vous pouvez utiliser la **tri** propriété pour définir l’ordre dans les lignes d’un **Recordset** sont parcourus. En outre, le **filtre** propriété détermine les lignes qui sont accessibles lors du parcours des lignes.  
  
 Le **tri** propriété définit ou retourne un **chaîne** valeur qui indique le champ de noms dans le **Recordset** sur laquelle trier. Chaque nom est séparé par une virgule et éventuellement suivie d’un espace et le mot clé **ASC** (qui trie le champ dans l’ordre croissant) ou **DESC** (qui trie le champ dans l’ordre décroissant). Par défaut, si aucun mot clé n’est spécifié, le champ est trié dans l’ordre croissant.  
  
 L’opération de tri est efficace, car les données ne sont pas physiquement réorganisées mais qu’il sont accessible dans l’ordre spécifié par un index.  
  
 Le **tri** propriété nécessite la [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété être définie sur **adUseClient**. Un index temporaire est créé pour chaque champ dans le **tri** propriété si un index n’existe pas déjà.  
  
 Définition de la **tri** propriété sur une chaîne vide sera réinitialise les lignes dans leur ordre d’origine et supprimer des index temporaires. Les index existants ne seront pas supprimés.  
  
 Supposons qu’un **Recordset** contient trois champs nommés *firstName*, *middleInitial*, et *lastName*. Définir le **tri** propriété à la chaîne de «`lastName DESC, firstName ASC`», sera le **Recordset** par nom de famille dans l’ordre décroissant, puis par prénom par ordre croissant. L’initiale du milieu est ignoré.  
  
 Aucun champ référencé dans une chaîne de critères de tri ne peut être nommé « ASC » ou « DESC », car ces noms en conflit avec les mots clés **ASC** et **DESC**. Donnez à un champ qui porte un nom en conflit un alias à l’aide de la **AS** mot clé dans la requête qui retourne le **Recordset**.  
  
 Pour plus d’informations sur **Recordset** filtrage, consultez « Filtrage des résultats » plus loin dans cette rubrique.  
  
## <a name="finding-a-specific-record"></a>Recherche un enregistrement spécifique  
 ADO fournit le [trouver](../../../ado/reference/ado-api/find-method-ado.md) et [recherche](../../../ado/reference/ado-api/seek-method.md) méthodes pour localiser un enregistrement particulier dans un **Recordset**. Le **trouver** méthode est pris en charge par un grand nombre de fournisseurs, mais est limitée à un seul critère de recherche. Le **recherche** méthode prend en charge la recherche sur plusieurs critères, mais n’est pas pris en charge par de nombreux fournisseurs.  
  
 Champs indexés peuvent améliorer considérablement les performances de la **trouver** (méthode) et **tri** et **filtre** propriétés de la **Recordset** objet. Vous pouvez créer un index interne pour un **champ** objet en définissant son dynamique [optimiser](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) propriété. Cette propriété dynamique est ajoutée à la **propriétés** collection de la **champ** de l’objet lorsque vous définissez la [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété **adUseClient**. N’oubliez pas que cet index est interne à ADO : vous ne pouvez pas y accéder ou l’utiliser à d’autres fins. En outre, cet index est différent de la [Index](../../../ado/reference/ado-api/index-property.md) propriété de la **Recordset** objet.  
  
 Le **trouver** méthode localiser rapidement une valeur dans la colonne (champ) d’un **Recordset**. Vous pouvez souvent améliorer la vitesse de la **trouver** méthode sur une colonne à l’aide de la **optimiser** propriété pour créer un index sur celle-ci.  
  
 Le **trouver** méthode limite votre recherche au contenu d’un champ. Le **recherche** méthode requiert que vous avez un index et présente également d’autres limitations. Si vous devez effectuer une recherche sur plusieurs champs qui ne sont pas la base d’un index, ou si votre fournisseur ne prend pas en charge les index, vous pouvez limiter vos résultats à l’aide de la **filtre** propriété de la **Recordset** objet.  
  
### <a name="find"></a>Rechercher  
 Le **trouver** méthode recherche une **Recordset** pour la ligne répondant à un critère spécifié. Si vous le souhaitez, la direction de recherche, de ligne de début et de décalage à partir de la ligne initiale peut être spécifiée. Si le critère est rempli, la position de ligne actuelle est définie sur l’enregistrement est trouvé ; Sinon, la position est définie à la fin (ou le début) de la **Recordset**, selon la direction de la recherche.  
  
 Uniquement un seul nom de colonne peut être spécifié pour le critère. En d’autres termes, cette méthode ne prend pas en charge les recherches sur plusieurs colonnes.  
  
 L’opérateur de comparaison pour le critère peut être " **>** " (supérieur à), " **\<** " (inférieur à), « = » (égal), « > = » (supérieur ou égal à), « < = » (inférieur ou égal à), » <> » (différent de), ou « LIKE » (critères spéciaux).  
  
 La valeur du critère peut être une chaîne, un nombre à virgule flottante ou une date. Valeurs de chaîne sont délimitées par des guillemets simples ou « # » (signe dièse) (par exemple, « état = 'WA' » ou « état = #WA # »). Valeurs de date sont séparés par des signes « # » (signe dièse) (par exemple, « start_date > #7/22/97 # »).  
  
 Si l’opérateur de comparaison est « like », la valeur de chaîne peut contenir un astérisque (*) pour rechercher une ou plusieurs occurrences de n’importe quel caractère ou une sous-chaîne. Par exemple, « state like'm\*' » correspond à Maine et du Massachusetts. Vous pouvez également utiliser des astérisques de début et de fin pour rechercher une sous-chaîne contenue dans les valeurs. Par exemple, « état comme '\*comme\*' » correspond à Alaska, Arkansas et Massachusetts.  
  
 Astérisques peuvent être utilisés uniquement à la fin d’une chaîne de critères ou conjointement au début et à la fin d’une chaîne de critères, comme indiqué précédemment. Vous ne pouvez pas utiliser l’astérisque comme caractère générique de début ('* str') ou incorporé s\*r »). Cela entraîne une erreur.  
  
### <a name="seek-and-index"></a>Rechercher et d’Index  
 Utilisez le **recherche** méthode avec le **Index** propriété si le fournisseur sous-jacent prend en charge les index sur la **Recordset** objet. Utilisez le [prend en charge](../../../ado/reference/ado-api/supports-method.md) **(adSeek)** méthode pour déterminer si le fournisseur sous-jacent prend en charge **recherche**et le **supports (adIndex)** méthode pour déterminer si le fournisseur prend en charge les index. (Par exemple, le [fournisseur OLE DB pour Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) prend en charge **recherche** et **Index**.)  
  
 Si **recherche** n’a pas de rechercher la ligne souhaitée, aucune erreur ne se produit et la ligne est placé à la fin de la **Recordset**. Définir le **Index** index à la propriété souhaitée avant d’exécuter cette méthode.  
  
 Cette méthode est prise en charge uniquement avec les curseurs côté serveur. Seek n’est pas pris en charge lorsque le [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) valeur de propriété de la **Recordset** objet est **adUseClient**.  
  
 Cette méthode peut être utilisée uniquement lorsque la **Recordset** objet a été ouvert avec un [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) valeur **adCmdTableDirect**.  
  
## <a name="filtering-the-results"></a>Filtrage des résultats  
 Le **trouver** méthode limite votre recherche au contenu d’un champ. Le **recherche** méthode requiert que vous avez un index et présente également d’autres limitations. Si vous devez effectuer une recherche sur plusieurs champs qui ne sont pas la base d’un index ou si votre fournisseur ne prend pas en charge les index, vous pouvez limiter vos résultats à l’aide de la **filtre** propriété de la **Recordset** objet.  
  
 Utilisez le **filtre** propriété à filtrer les enregistrements dans une **Recordset** objet. Filtrés **Recordset** devient le curseur actuel, ce qui signifie que les enregistrements qui ne respecte pas la **filtre** critères ne sont pas disponibles dans le **Recordset** jusqu'à ce que le **Filtre** est supprimé. Autres propriétés qui retournent des valeurs basées sur le curseur actuel sont affectées, tel que **AbsolutePosition**, **AbsolutePage**, **RecordCount**, et  **PageCount**. Il s’agit, car l’affectation du **filtre** propriété sur une valeur spécifique déplacera l’enregistrement actif vers le premier enregistrement qui satisfait à la nouvelle valeur.  
  
 Le **filtre** propriété accepte un argument de type variant. Cette valeur représente une des trois méthodes pour l’utilisation de la **filtre** propriété : une chaîne de critères, une **FilterGroupEnum** constante ou un tableau de signets. Pour plus d’informations, consultez filtrage avec une chaîne de critères de filtrage avec une constante et filtrage avec des signets, plus loin dans cette rubrique.  
  
> [!NOTE]
>  Lorsque vous connaissez les données que vous souhaitez sélectionner, il est généralement plus efficace pour ouvrir un **Recordset** avec une instruction SQL qui permet de filtrer efficacement le jeu de résultats, au lieu d’utiliser le **filtre** propriété.  
  
 Pour supprimer un filtre à partir d’un **Recordset**, utilisez le **adFilterNone** constante. Définissant le **filtre** en une chaîne de longueur nulle (« ») a le même effet que l’utilisation de la **adFilterNone** constante.  
  
### <a name="filtering-with-a-criteria-string"></a>Filtrage avec une chaîne de critères  
 La chaîne de critères se compose de clauses sous la forme *NomChamp Opérateur valeur* (par exemple, `"LastName = 'Smith'"`). Vous pouvez créer des clauses composées en concaténant des clauses avec **AND** (par exemple, `"LastName = 'Smith' AND FirstName = 'John'"`) et **ou** (par exemple, `"LastName = 'Smith' OR LastName = 'Jones'"`). Utilisez les instructions suivantes pour les chaînes de critères :  
  
-   *FieldName* doit être un nom de champ valide à partir de la **Recordset**. Si le nom du champ contienne des espaces, vous devez placer le nom entre crochets.  
  
-   *Opérateur* doit être une des opérations suivantes : **\<** , **>** , **\< =** , **>=** , **<>** , **=** , ou **comme**.  
  
-   *Valeur* est la valeur avec laquelle vous allez comparer les valeurs de champ (par exemple, `'Smith'`, `#8/24/95#`, `12.345`, ou `$50.00`). Utilisez des guillemets simples (') avec des chaînes et les signes dièse (`#`) avec des dates. Pour les nombres, vous pouvez utiliser décimales, signes dollar et la notation scientifique. Si *opérateur* est **comme**, *valeur* peut utiliser des caractères génériques. Uniquement l’astérisque (\*) et symbole de pourcentage (%) caractères génériques sont autorisés, et ils doivent être le dernier caractère de la chaîne. *Valeur* ne peut pas être null.  
  
    > [!NOTE]
    >  Pour inclure des guillemets simples (') dans le filtre *valeur*, utilisez deux guillemets simples pour représenter un. Par exemple, pour filtrer sur *o ' Malley*, la chaîne de critères doit être `"col1 = 'O''Malley'"`. Pour inclure des guillemets simples au début et la fin de la valeur de filtre, placer la chaîne entre les signes dièse (#). Par exemple, pour filtrer sur *'1'* , la chaîne de critères doit être `"col1 = #'1'#"`.  
  
 Il n’existe aucun ordre de priorité **AND** et **ou**. Clauses peuvent être regroupées dans les parenthèses. Toutefois, vous ne pouvez pas regrouper des clauses jointes par une **ou** puis joindre le groupe à une autre clause avec un AND, comme suit.  
  
```  
(LastName = 'Smith' OR LastName = 'Jones') AND FirstName = 'John'  
```  
  
 Au lieu de cela, vous devez construire ce filtre comme suit.  
  
```  
(LastName = 'Smith' AND FirstName = 'John') OR (LastName = 'Jones' AND FirstName = 'John')  
```  
  
 Dans un **comme** clause, vous pouvez utiliser un caractère générique au début et à la fin du modèle (par exemple, `LastName Like '*mit*'`) ou uniquement à la fin du modèle (par exemple, `LastName Like 'Smit*'`).  
  
### <a name="filtering-with-a-constant"></a>Filtrage avec une constante  
 Les constantes suivantes sont disponibles pour le filtrage **Recordsets**.  
  
|Constante|Description|  
|--------------|-----------------|  
|**adFilterAffectedRecords**|Filtres pour afficher uniquement les enregistrements concernés par la dernière **supprimer**, **Resync**, **UpdateBatch**, ou **CancelBatch** appeler.|  
|**adFilterConflictingRecords**|Filtres pour afficher les enregistrements qui ont échoué la dernière mise à jour par lots.|  
|**adFilterFetchedRecords**|Filtres pour afficher les enregistrements dans le cache actuel - autrement dit, les résultats du dernier appel pour récupérer les enregistrements à partir de la base de données.|  
|**adFilterNone**|Supprime le filtre en cours et restaure tous les enregistrements pour l’affichage.|  
|**adFilterPendingRecords**|Filtres pour afficher uniquement les enregistrements qui ont été modifiés, mais qui n’ont pas encore été envoyées au serveur. Applicable uniquement pour le mode de mise à jour par lot.|  
  
 Les constantes de filtre facilitent la résolution des conflits d’enregistrements individuels lors des mises à jour par lot en vous permettant d’afficher, par exemple, uniquement les enregistrements qui ont été affectés pendant la dernière **UpdateBatch** appel de méthode, comme indiqué dans le exemple suivant.  
  
 `Attribute VB_Name = "modExaminingData"`  
  
### <a name="filtering-with-bookmarks"></a>Filtrage avec des signets  
 Enfin, vous pouvez passer un tableau de type variant de signets pour les **filtre** propriété. Le curseur résultant contiendra uniquement les enregistrements dont le signet a été passé à la propriété. L’exemple de code suivant crée un tableau de signets à partir des enregistrements dans une **Recordset** qui ont un « B » dans le *ProductName* champ. Il passe ensuite le tableau à la **filtre** propriété et affiche des informations sur le résultat filtré **Recordset**.  
  
```  
'BeginFilterBkmk  
Dim vBkmkArray() As Variant  
Dim i As Integer  
  
'Recordset created using "SELECT * FROM Products" as command.  
'So, we will check to see if ProductName has a capital B, and  
'if so, add to the array.  
i = 0  
Do While Not objRs.EOF  
    If InStr(1, objRs("ProductName"), "B") Then  
        ReDim Preserve vBkmkArray(i)  
        vBkmkArray(i) = objRs.Bookmark  
        i = i + 1  
        Debug.Print objRs("ProductName")  
    End If  
    objRs.MoveNext  
Loop  
  
'Filter using the array of bookmarks.  
objRs.Filter = vBkmkArray  
  
objRs.MoveFirst  
Do While Not objRs.EOF  
    Debug.Print objRs("ProductName")  
    objRs.MoveNext  
Loop  
'EndFilterBkmk  
```  
  
## <a name="creating-a-clone-of-a-recordset"></a>Création d’un Clone d’un Recordset  
 Utilisez le **Clone** dupliqué de la méthode de création de plusieurs **Recordset** objets, en particulier si vous voulez conserver plusieurs enregistrements en cours dans un ensemble donné d’enregistrements. À l’aide de la **Clone** méthode est plus efficace que la création et ouverture d’un nouvel **Recordset** objet avec la même définition que l’original.  
  
 L’enregistrement en cours d’un clone nouvellement créé est initialement défini sur le premier enregistrement. Le pointeur d’enregistrement actuel dans cloné **Recordset** n’est pas synchronisé avec l’original, ou vice versa. Vous pouvez naviguer de manière indépendante dans chaque **Recordset**.  
  
 Modifications apportées à un **Recordset** objet sont visibles dans tous ses clones, quel que soit le type de curseur. Toutefois, après l’exécution de [Requery](../../../ado/reference/ado-api/requery-method.md) sur l’original **Recordset**, les clones ne seront plus synchronisés à l’original.  
  
 Fermeture de la version d’origine **Recordset** ne ferme pas ses copies, ni ne le fait fermeture d’une copie de fermer la version d’origine ou les autres copies.  
  
 Vous pouvez cloner un **Recordset** uniquement l’objet si elle prend en charge les signets. Les valeurs de signet sont interchangeables ; Autrement dit, une référence de signet à partir d’un **Recordset** objet fait référence au même enregistrement dans un de ses clones.
