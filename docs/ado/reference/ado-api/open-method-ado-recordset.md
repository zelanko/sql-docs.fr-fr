---
title: Open, méthode (objet Recordset ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_Open
- Recordset15::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: 3236749c-4b71-4235-89e2-ccdfaaa9319d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dc084a4fc2d5448efce8721c426ce78a4bb18a76
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47655517"
---
# <a name="open-method-ado-recordset"></a>Open, méthode (objet Recordset ADO)
Ouvre un curseur sur une [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
recordset.Open Source, ActiveConnection, CursorType, LockType, Options  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Source*  
 Facultatif. Un **Variant** qui prend la valeur valide [commande](../../../ado/reference/ado-api/command-object-ado.md) objet, une instruction SQL, un nom de table, un appel de procédure stockée, une URL ou le nom d’un fichier ou [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objet contenant un stocké de manière permanente [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 *ActiveConnection*  
 Facultatif. Soit un **Variant** qui prend la valeur valide [connexion](../../../ado/reference/ado-api/connection-object-ado.md) nom de la variable objet, ou un **chaîne** contenant [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) paramètres.  
  
 *CursorType*  
 Facultatif. Un [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md) valeur qui détermine le type de curseur que le fournisseur doit utiliser lors de l’ouverture du **Recordset**. La valeur par défaut est **adOpenForwardOnly**.  
  
 *LockType*  
 Facultatif. Un [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) valeur qui détermine le type de verrouillage (accès concurrentiel) que le fournisseur doit utiliser lors de l’ouverture du **Recordset**. La valeur par défaut est **adLockReadOnly**.  
  
 *Options*  
 Facultatif. Un **Long** valeur qui indique la manière dont le fournisseur doit évaluer le *Source* argument si elle représente un élément autre qu’un **commande** objet, ou qui le **Recordset** doit être restauré à partir d’un fichier dans lequel il a été précédemment enregistré. Peut être un ou plusieurs [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) ou [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) valeurs, qui peuvent être combinées avec un opérateur OR au niveau du bit.  
  
> [!NOTE]
>  Si vous ouvrez un **Recordset** à partir d’un **Stream** contenant un persistantes **Recordset**, à l’aide un [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) valeur **adAsyncFetchNonBlocking** n’a aucun effet ; l’extraction sera synchrone et bloquante.  
  
> [!NOTE]
>  Le **ExecuteOpenEnum** les valeurs de **adExecuteStream** ou **adExecuteStream** ne doit pas être utilisé avec **Open**.  
  
## <a name="remarks"></a>Notes  
 Le curseur par défaut pour ADO **Recordset** est un curseur avant uniquement et en lecture seule situé sur le serveur.  
  
 À l’aide de la **Open** méthode sur un **Recordset** objet ouvre un curseur qui représente des enregistrements d’une table de base, les résultats d’une requête ou précédemment enregistré **Recordset**.  
  
 Utilisez le paramètre facultatif *Source* argument pour spécifier une source de données à l’aide d’un des éléments suivants : un **commande** variable objet, une instruction SQL, une procédure stockée, un nom de table, une URL ou un nom de chemin d’accès complet du fichier. Si *Source* est un nom de chemin d’accès de fichier, il peut être un chemin d’accès complet (« c:\dir\file.rst »), d’un chemin d’accès relatif («.. \file.rst »), ou une URL (« http://files/file.rst»).  
  
 Il n’est pas une bonne idée d’utiliser le *Source* argument de la **Open** méthode pour effectuer une requête d’action qui ne retourne pas d’enregistrements, car il n’existe aucun moyen facile de déterminer si l’appel a réussi. Le **Recordset** retourné par ce type une requête va être fermée. Pour effectuer une requête qui ne retourne pas d’enregistrements, telle qu’une instruction SQL INSERT, appelez le [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) méthode d’un **commande** objet ou le [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) méthode d’un [Connexion](../../../ado/reference/ado-api/connection-object-ado.md) à la place de l’objet.  
  
 Le *ActiveConnection* argument correspond à la [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) propriété et spécifie la connexion dans laquelle ouvrir le **Recordset** objet. Si vous transmettez une définition de la connexion pour cet argument, ADO ouvre une nouvelle connexion à l’aide des paramètres spécifiés. Après avoir ouvert le **Recordset** avec un curseur côté client en définissant le [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété **adUseClient**, vous pouvez modifier la valeur de cette propriété pour envoyer mises à jour vers un autre fournisseur. Ou vous pouvez définir cette propriété sur **rien** (dans Microsoft Visual Basic) ou NULL pour déconnecter le **Recordset** à partir de n’importe quel fournisseur. Modification *ActiveConnection* pour un curseur côté serveur génère une erreur, toutefois.  
  
 Pour les autres arguments correspondent directement aux propriétés d’un **Recordset** objet (*Source*, *CursorType*, et *LockType*), la relation entre les arguments et les propriétés est comme suit :  
  
-   La propriété est en lecture/écriture avant la **Recordset** objet est ouvert.  
  
-   Les paramètres de propriété sont utilisées, sauf si vous passez les arguments correspondants lors de l’exécution le **Open** (méthode). Si vous passez un argument, elle remplace le paramètre de propriété correspondant et le paramètre de propriété est mis à jour avec la valeur d’argument.  
  
-   Après avoir ouvert le **Recordset** de l’objet, ces propriétés deviennent en lecture seule.  
  
> [!NOTE]
>  Le **ActiveConnection** propriété est en lecture seule pour **Recordset** objets dont la propriété [Source](../../../ado/reference/ado-api/source-property-ado-recordset.md) propriété est définie sur valide **commande** objet, même si le **Recordset** objet n’est pas ouvert.  
  
 Si vous passez un **commande** de l’objet dans le *Source* argument et également passez un *ActiveConnection* argument, une erreur se produit. Le **ActiveConnection** propriété de la **commande** objet doit déjà être défini sur valide **connexion** objet ou chaîne de connexion.  
  
 Si vous passez un élément autre qu’un **commande** de l’objet dans le *Source* argument, vous pouvez utiliser la *Options* argument pour optimiser l’évaluation de la *Source*  argument. Si le *Options* argument n’est pas défini, vous pouvez rencontrer des performances diminuent, car ADO doit effectuer des appels au fournisseur pour déterminer si l’argument est une instruction SQL, une procédure stockée, une URL ou un nom de table. Si vous savez *Source* type que vous utilisez, définissant le *Options* argument indique à ADO d’accéder directement au code approprié. Si le *Options* argument ne correspond pas à la *Source* type, une erreur se produit.  
  
 Si vous passez un **Stream** de l’objet dans le *Source* argument, vous ne passez pas d’informations dans les autres arguments. Cela générera une erreur. Le **ActiveConnection** informations ne sont pas conservées quand un **Recordset** est ouvert à partir d’un **Stream**.  
  
 La valeur par défaut pour le *Options* argument est **adCmdFile** si aucune connexion n’est associée à la **Recordset**. Ce sera généralement le cas pour stocké de manière permanente **Recordset** objets.  
  
 Si la source de données ne renvoie aucun enregistrement, le fournisseur définit à la fois le [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) et [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) propriétés à **True**, et la position actuelle n’est pas définie. Vous pouvez toujours ajouter de nouvelles données à ce vide **Recordset** si le type de curseur permet de l’objet.  
  
 Lorsque vous avez terminé les opérations au moyen d’un **Recordset** de l’objet, utilisez le [fermer](../../../ado/reference/ado-api/close-method-ado.md) méthode pour libérer les ressources système d’associées. Fermeture d’un objet ne le supprime pas de la mémoire. Vous pouvez modifier ses paramètres de propriété et utiliser le **ouvrir** méthode pour l’ouvrir à nouveau ultérieurement. Pour éliminer complètement un objet de la mémoire, la valeur est la variable objet *rien*.  
  
 Avant du **ActiveConnection** propriété est définie, appelez **Open** sans opérande pour créer une instance d’un **Recordset** créé en ajoutant des champs à la  **Jeu d’enregistrements** [champs](../../../ado/reference/ado-api/fields-collection-ado.md) collection.  
  
 Si vous avez défini le [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété **adUseClient**, vous pouvez récupérer des lignes de façon asynchrone de deux manières. La méthode recommandée consiste à définir *Options* à **adAsyncFetch**. Vous pouvez également utiliser la propriété dynamique « Ensemble de lignes Asynchronous Processing » dans la [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection, mais les événements récupérés peuvent être perdues si vous ne définissez pas la *Options* paramètre **adAsyncFetch**.  
  
> [!NOTE]
>  L’extraction en arrière-plan dans le fournisseur MS Remote est pris en charge uniquement via le **Open** la méthode *Options* paramètre.  
  
> [!NOTE]
>  URL à l’aide du modèle http appellent automatiquement le [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Pour plus d’informations, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 Certaines combinaisons de [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) et [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) valeurs ne sont pas valides. Pour plus d’informations sur les options ne peuvent pas être combinées, consultez les rubriques pour le [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md), et [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Les méthodes Open et Close, exemple (VB)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Les méthodes Open et Close, exemple (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Les méthodes Open et Close, exemple (VC ++)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Enregistrer et ouvrir des exemples de méthodes (VB)](../../../ado/reference/ado-api/save-and-open-methods-example-vb.md)   
 [Open, méthode (objet Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open, méthode (objet Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open, méthode (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [OpenSchema, méthode](../../../ado/reference/ado-api/openschema-method.md)   
 [Save, méthode](../../../ado/reference/ado-api/save-method.md)
