---
title: Save, méthode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Recordset::Save
- _Recordset::raw_Save
helpviewer_keywords:
- Save method [ADO]
ms.assetid: ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 55ba7b2fc9e1b6ea0eaeb44989e1bfb64b44d9d4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63315209"
---
# <a name="save-method"></a>Save, méthode
Enregistre le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) dans un fichier ou [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
recordset.Save Destination, PersistFormat  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Destination*  
 Facultatif. Un **Variant** qui représente le nom de chemin d’accès complet du fichier où le **Recordset** doit être enregistré, ou une référence à un **Stream** objet.  
  
 *PersistFormat*  
 Facultatif. Un [PersistFormatEnum](../../../ado/reference/ado-api/persistformatenum.md) valeur qui spécifie le format dans lequel le **Recordset** doit être enregistré (XML ou ADTG). La valeur par défaut est **adPersistADTG**.  
  
## <a name="remarks"></a>Notes  
 Le [méthode Save](../../../ado/reference/ado-api/save-method.md) méthode peut uniquement être appelée sur une ouverte **Recordset**. Utilisez le [méthode Open (objet Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md) méthode à la restauration ultérieure le **Recordset** à partir de *Destination*.  
  
 Si le [propriété Filter](../../../ado/reference/ado-api/filter-property.md) propriété est en vigueur pour le **Recordset**, seules les lignes accessibles sous le filtre sont enregistrées. Si le **Recordset** est hiérarchique, puis l’enfant actuel **Recordset** et ses enfants sont enregistrés, y compris le parent **Recordset**. Si la méthode Save d’un enfant **Recordset** est appelée, l’enfant et tous ses enfants sont enregistrés, mais le parent n’est pas.  
  
 La première fois que vous enregistrez le **Recordset**, il est facultatif pour spécifier *Destination*. Si vous omettez *Destination*, un nouveau fichier sera créé avec un nom défini sur la valeur de la propriété de Source de la **Recordset**.  
  
 Omettez *Destination* lorsque vous appelez ensuite **enregistrer** après le premier enregistrement, ou une erreur d’exécution se produira. Si vous appelez ensuite **enregistrer** avec un nouveau *Destination*, le **Recordset** est enregistré dans la nouvelle destination. Toutefois, la nouvelle destination et la destination d’origine seront tous deux être ouverts.  
  
 **Enregistrer** ne ferme pas la **Recordset** ou *Destination*, de sorte que vous pouvez continuer à travailler avec le **Recordset** et enregistrer vos modifications les plus récentes. *Destination* reste ouverte jusqu'à ce que le **Recordset** est fermé.  
  
 Pour des raisons de sécurité, le **enregistrer** méthode autorise uniquement l’utilisation des paramètres de sécurité basse et personnalisée à partir d’un script exécuté par Microsoft Internet Explorer.  
  
 Si le **enregistrer** méthode est appelée lors de l’asynchrone **Recordset** extraire, exécuter ou mettre à jour opération est en cours, puis **enregistrer** attend que l’opération asynchrone est terminée.  
  
 Les enregistrements sont enregistrés en commençant par la première ligne de la **Recordset**. Lorsque le **enregistrer** méthode est terminée, le curseur est déplacé vers la première ligne de la **Recordset**.  
  
 Pour de meilleurs résultats, définissez le [CursorLocation propriété (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété **adUseClient** avec **enregistrer**. Si votre fournisseur ne prend pas en charge toutes les fonctionnalités nécessaires pour enregistrer les **Recordset** objets, le Service de curseur fournit cette fonctionnalité.  
  
 Quand un **Recordset** est rendue persistante avec le **CursorLocation** propriété définie sur **adUseServer**, la fonctionnalité de mise à jour pour le **Recordset**est limité. En règle générale, seules les mises à jour de la table unique, des insertions et suppressions sont autorisées (selon les fonctionnalités du fournisseur). Le [méthode Resync](../../../ado/reference/ado-api/resync-method.md) méthode est également pas disponible dans cette configuration.  
  
> [!NOTE]
>  Enregistrer un **Recordset** avec **champs** de type **adVariant**, **adIDispatch**, ou **adIUnknown** est non pris en charge par ADO et peut entraîner des résultats imprévisibles.  
  
 Filtre uniquement sous la forme de chaînes de critères (par exemple OrderDate > ' 12/31/1999 ') affectent le contenu d’un rendu persistant **Recordset**. Les filtres créés avec un tableau de **signets** ou à l’aide d’une valeur comprise entre le [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md) n’affectera pas le contenu du rendu persistant **Recordset**. Ces règles s’appliquent aux **Recordset**s créés avec les curseurs côté client ou côté serveur.  
  
 Étant donné que le *Destination* paramètre peut accepter n’importe quel objet qui prend en charge l’interface OLE DB IStream, vous pouvez enregistrer un **Recordset** directement à l’objet de réponse de ASP. Pour plus d’informations, consultez le **scénario de persistance XML Recordset**.  
  
 Vous pouvez également enregistrer un **Recordset** au format XML à une instance d’un objet DOM MSXML, comme est indiqué dans le code Visual Basic suivant :  
  
```  
Dim xDOM As New MSXML.DOMDocument  
Dim rsXML As New ADODB.Recordset  
Dim sSQL As String, sConn As String  
  
sSQL = "SELECT customerid, companyname, contactname FROM customers"  
sConn="Provider=Microsoft.Jet.OLEDB.4.0;Data Source=Northwind.mdb"  
rsXML.Open sSQL, sConn  
rsXML.Save xDOM, adPersistXML   'Save Recordset directly into a DOM tree.  
...  
```  
  
> [!NOTE]
>  Deux limitations s’appliquent lors de l’enregistrement des jeux d’enregistrements (formes de données) au format XML. Vous ne pouvez pas enregistrer au format XML si l’hiérarchique **Recordset** contient en attente de mises à jour, et vous ne pouvez pas enregistrer un paramétrable hiérarchique **Recordset**.  
  
 Un **Recordset** enregistré au format XML format est enregistré à l’aide du format UTF-8. Lorsqu’un tel fichier est chargé dans un Stream ADO, l’objet Stream ne tentera pas d’ouvrir un **Recordset** à partir du flux, sauf si la propriété de jeu de caractères du flux est définie à la valeur appropriée pour le format UTF-8.  
  
## <a name="applies-to"></a>S'applique à  
  
|||  
|-|-|  
|[Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer et ouvrir des exemples de méthodes (VB)](../../../ado/reference/ado-api/save-and-open-methods-example-vb.md)   
 [Enregistrer et ouvrir l’exemple de méthodes (VC ++)](../../../ado/reference/ado-api/save-and-open-methods-example-vc.md)   
 [Open, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open, méthode (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [SaveToFile, méthode](../../../ado/reference/ado-api/savetofile-method.md)
