---
title: Fournisseur Microsoft OLE DB pour le service d’indexation Microsoft | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Indexing Service provider [ADO]
- providers [ADO], OLE DB provider for Microsoft Indexing service
- OLE DB provider for Microsoft Indexing service [ADO]
ms.assetid: f86a0598-5097-471b-8318-d2c859d085f2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a5a81514fd12117a9f43e2c33bf0cda579fb363d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926664"
---
# <a name="microsoft-ole-db-provider-for-microsoft-indexing-service-overview"></a>Vue d’ensemble du fournisseur Microsoft OLE DB pour le service d’indexation Microsoft
Le fournisseur Microsoft OLE DB pour le service d’indexation Microsoft fournit un accès par programmation en lecture seule au système de fichiers et aux données Web indexées par le service d’indexation Microsoft. Les applications ADO peuvent émettre des requêtes SQL pour récupérer du contenu et des informations sur les propriétés de fichier.

 Le fournisseur est libre de thread et UNICODE est activé.

## <a name="connection-string-parameters"></a>Paramètres de chaîne de connexion
 Pour vous connecter à ce fournisseur, affectez à l’argument **Provider =** la valeur de la propriété [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) :

```vb
MSIDXS
```

 La lecture de la propriété [Provider](../../../ado/reference/ado-api/provider-property-ado.md) retourne également cette chaîne.

## <a name="typical-connection-string"></a>Chaîne de connexion classique
 Une chaîne de connexion classique pour ce fournisseur est la suivante :

```vb
"Provider=MSIDXS;Data Source=myCatalog;Locale Identifier=nnnn;"
```

 La chaîne se compose des mots clés suivants :

|Mot clé|Description|
|-------------|-----------------|
|**Fournisseur**|Spécifie le fournisseur de OLE DB pour le service d’indexation Microsoft. En général, il s’agit du seul mot clé spécifié dans la chaîne de connexion.|
|**Source de données**|Spécifie le nom du catalogue du service d’indexation. Si ce mot clé n’est pas spécifié, le catalogue système par défaut est utilisé.|
|**Identificateur de paramètres régionaux**|Spécifie un nombre 32 bits unique (par exemple, 1033) qui spécifie les préférences relatives à la langue de l’utilisateur. Si ce mot clé n’est pas spécifié, l’identificateur de paramètres régionaux par défaut est utilisé.|

## <a name="command-text"></a>Texte de la commande
 La syntaxe de requête SQL du service d’indexation se compose d’extensions de l’instruction SQL-92 **Select** et de ses clauses **from** et **Where** . Les résultats de la requête sont retournés via OLE DB ensembles de lignes, qui peuvent être consommés par ADO et manipulés en tant qu’objets [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) .

 Vous pouvez rechercher des mots ou expressions exacts, ou utiliser des caractères génériques pour rechercher des modèles ou des tiges de mots. La logique de recherche peut être basée sur des décisions booléennes, des termes pondérés ou une proximité à d’autres mots. Vous pouvez également effectuer une recherche en « texte libre », qui recherche les correspondances en fonction de la signification, plutôt que des mots exacts.

 Le dialecte de la commande spécifique est entièrement documenté dans la documentation des langages de requête pour le service d’indexation.

 Le fournisseur n’accepte pas les appels de procédure stockée ou les noms de tables simples (par exemple, la propriété [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) sera toujours **adCmdText**).

## <a name="recordset-behavior"></a>Comportement du Recordset
 Les tableaux suivants répertorient les fonctionnalités disponibles avec un objet **Recordset** ouvert avec ce fournisseur. Seul le type de curseur statique (**adOpenStatic**) est disponible.

 Pour plus d’informations sur le comportement du **Recordset** pour la configuration de votre fournisseur, exécutez la méthode [supports](../../../ado/reference/ado-api/supports-method.md) et Énumérez la collection [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) du **Recordset** pour déterminer si des propriétés dynamiques spécifiques au fournisseur sont présentes.

 **Disponibilité des propriétés standard du Recordset ADO :**

|Propriété|Disponibilité|
|--------------|------------------|
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|lecture/écriture|
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|lecture/écriture|
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|en lecture seule|
|[Business](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|en lecture seule|
|[Signet](../../../ado/reference/ado-api/bookmark-property-ado.md)*|lecture/écriture|
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|lecture/écriture|
|[Ait](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|toujours **adUseServer**|
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|toujours **adOpenStatic**|
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|toujours **adEditNone**|
|[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|en lecture seule|
|[Filter](../../../ado/reference/ado-api/filter-property.md)|lecture/écriture|
|[Verrou](../../../ado/reference/ado-api/locktype-property-ado.md)|lecture/écriture|
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|non disponible|
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|lecture/écriture|
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|en lecture seule|
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|lecture/écriture|
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|en lecture seule|
|[Source](../../../ado/reference/ado-api/source-property-ado-recordset.md)|lecture/écriture|
|[State](../../../ado/reference/ado-api/state-property-ado.md)|en lecture seule|
|[État](../../../ado/reference/ado-api/status-property-ado-recordset.md)|en lecture seule|

 \*Les signets doivent être activés sur le fournisseur afin que cette fonctionnalité existe sur le **Recordset**.

 **Disponibilité des méthodes de l’ensemble d’enregistrements ADO standard :**

|Méthode|Téléchargé?|
|------------|----------------|
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|Non|
|[Annuler](../../../ado/reference/ado-api/cancel-method-ado.md)|Oui|
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Non|
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Non|
|[Répliqué](../../../ado/reference/ado-api/clone-method-ado.md)|Oui|
|[Plus](../../../ado/reference/ado-api/close-method-ado.md)|Oui|
|[Supprimer](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Non|
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Oui|
|[Déplacer](../../../ado/reference/ado-api/move-method-ado.md)|Oui|
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Oui|
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|Oui|
|[Ouvrir](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Oui|
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Oui|
|[Resynchroniser](../../../ado/reference/ado-api/resync-method.md)|Oui|
|[Prise en charge](../../../ado/reference/ado-api/supports-method.md)|Oui|
|[Mise à jour](../../../ado/reference/ado-api/update-method.md)|Non|
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|Non|

 Pour obtenir des détails d’implémentation spécifiques et des informations fonctionnelles sur le fournisseur Microsoft OLE DB pour le service d’indexation Microsoft, consultez le [Guide du programmeur OLE DB](https://msdn.microsoft.com/library/windows/desktop/ms713643.aspx)ou visitez la page services Web du site Web Windows NT Server.

## <a name="see-also"></a>Voir aussi
 [CommandType, propriété (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md) [ConnectionString, propriété (ADO](../../../ado/reference/ado-api/connectionstring-property-ado.md) [) Properties collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [Provider, propriété](../../../ado/reference/ado-api/provider-property-ado.md) (ADO) [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [prend en charge la méthode](../../../ado/reference/ado-api/supports-method.md)
