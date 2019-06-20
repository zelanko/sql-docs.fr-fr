---
title: Fournisseur Microsoft OLE DB pour le Service Microsoft Active Directory | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADSI provider [ADO]
- Active Directory Service Interfaces provider [ADO]
- providers [ADO], OLE DB provider for Active Directory service
- OLE DB provider for Active Directory service [ADO]
ms.assetid: f9e81452-5675-4cfc-9949-cfbd2fe57534
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: acd7c73926e996100511569df3a5693068894b10
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702725"
---
# <a name="microsoft-ole-db-provider-for-microsoft-active-directory-service"></a>Fournisseur Microsoft OLE DB pour le Service Microsoft Active Directory
Le fournisseur Active Directory Service Interfaces (ADSI) permet à ADO pour se connecter à des services d’annuaire hétérogènes via ADSI. Ainsi, les applications ADO accès en lecture seule pour les services de répertoire Microsoft Windows NT 4.0 et Microsoft Windows 2000, en plus de n’importe quel service d’annuaire compatible LDAP et les Services d’annuaire Novell. ADSI en soi est basée sur un modèle de fournisseur, afin que s’il existe un nouveau fournisseur accorder l’accès à un autre répertoire, l’application ADO sera en mesure d’y accéder en toute transparence. Le fournisseur ADSI est libre de threads et Unicode.  
  
## <a name="connection-string-parameters"></a>Paramètres de chaîne de connexion  
 Pour vous connecter à ce fournisseur, définissez le **fournisseur** argument de la [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) suivante à la propriété :  
  
```vb
ADSDSOObject  
```  
  
 Lire le [fournisseur](../../../ado/reference/ado-api/provider-property-ado.md) propriété retournera cette forme de chaîne.  
  
## <a name="typical-connection-string"></a>Chaîne de connexion classique  
 Une chaîne de connexion classique pour ce fournisseur est la suivante :  
  
```vb
"Provider=ADSDSOObject;User ID=MyUserID;Password=MyPassword;"  
```  
  
 La chaîne se compose des mots-clés suivants.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|**Fournisseur**|Spécifie le fournisseur OLE DB pour le Service Active Directory.|  
|**ID d'utilisateur**|Spécifie le nom d’utilisateur. Si ce mot clé est omis, l’ouverture de session est utilisé.|  
|**Mot de passe**|Spécifie le mot de passe utilisateur. En l’absence de ce mot clé. L’ouverture de session est utilisé.|  
  
> [!NOTE]
>  Si vous vous connectez à un fournisseur de source de données qui prend en charge l’authentification Windows, vous devez spécifier **Trusted_Connection = yes** ou **Integrated Security = SSPI** au lieu des ID d’utilisateur et mot de passe informations dans la chaîne de connexion.  
  
## <a name="command-text"></a>Texte de la commande  
 Une chaîne de texte de commande en quatre parties est reconnue par le fournisseur dans la syntaxe suivante :  
  
```vb
"Root; Filter; Attributes[; Scope]"  
```  
  
|Value|Description|  
|-----------|-----------------|  
|*Root*|Indique le **ADsPath** objet à partir duquel commencer la recherche (autrement dit, la racine de la recherche).|  
|*Filter*|Indique le filtre de recherche au format RFC 1960.|  
|*Attributs*|Indique une liste délimitée par des virgules d’attributs à retourner.|  
|*Portée*|Facultatif. Un **chaîne** qui spécifie la portée de la recherche. Les valeurs possibles sont les suivantes :<br /><br /> -Base - rechercher uniquement l’objet de base (racine de la recherche).<br />-OneLevel - ne rechercher qu’un seul niveau.<br />-Sous-arborescence - recherche l’intégralité du sous-arbre.|  
  
 Exemple :  
  
```vb
"<LDAP://DC=ArcadiaBay,DC=COM>;(objectClass=*);sn, givenName; subtree"  
```  
  
 Le fournisseur prend également en charge SQL SELECT pour le texte de la commande. Exemple :  
  
```vb
"SELECT title, telephoneNumber From 'LDAP://DC=Microsoft, DC=COM' WHERE   
objectClass='user' AND objectCategory='Person'"  
```  
  
## <a name="remarks"></a>Notes  
 Le fournisseur n’accepte pas les appels de procédures stockées ou des noms de table simple (par exemple, le [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) propriété sera toujours **adCmdText**). Consultez la documentation d’Active Directory Service Interfaces pour obtenir une description plus détaillée des éléments de texte de commande.  
  
## <a name="recordset-behavior"></a>Comportement de jeu d’enregistrements  
 Les tableaux suivants répertorient les fonctionnalités disponibles sur un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet ouvert à l’aide de ce fournisseur. Seul le type de curseur statique (**adOpenStatic**) est disponible.  
  
 Pour plus d’informations sur **Recordset** comportement pour la configuration de votre fournisseur, exécutez le [prend en charge](../../../ado/reference/ado-api/supports-method.md) (méthode) et énumérer les [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection de la  **Jeu d’enregistrements** pour déterminer si les propriétés dynamiques spécifiques au fournisseur sont présentes.  
  
 **Disponibilité des propriétés de jeu d’enregistrements ADO standard :**  
  
|Propriété|Disponibilité|  
|--------------|------------------|  
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|lecture/écriture|  
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|lecture/écriture|  
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|Lecture seule|  
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|Lecture seule|  
|[Signet](../../../ado/reference/ado-api/bookmark-property-ado.md)|lecture/écriture|  
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|lecture/écriture|  
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|always **adUseServer**|  
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|always **adOpenStatic**|  
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|always **adEditNone**|  
|[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|Lecture seule|  
|[Filter](../../../ado/reference/ado-api/filter-property.md)|lecture/écriture|  
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|lecture/écriture|  
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|non disponible|  
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|lecture/écriture|  
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|Lecture seule|  
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|lecture/écriture|  
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|Lecture seule|  
|[Source](../../../ado/reference/ado-api/source-property-ado-recordset.md)|lecture/écriture|  
|[État](../../../ado/reference/ado-api/state-property-ado.md)|Lecture seule|  
|[État](../../../ado/reference/ado-api/status-property-ado-recordset.md)|Lecture seule|  
  
 **Disponibilité des méthodes de jeu d’enregistrements ADO standard :**  
  
|Méthode|Disponible ?|  
|------------|----------------|  
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|Non|  
|[Annuler](../../../ado/reference/ado-api/cancel-method-ado.md)|Non|  
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Non|  
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Non|  
|[Clone](../../../ado/reference/ado-api/clone-method-ado.md)|Oui|  
|[Fermer](../../../ado/reference/ado-api/close-method-ado.md)|Oui|  
|[Supprimer](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Non|  
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Oui|  
|[Déplacer](../../../ado/reference/ado-api/move-method-ado.md)|Oui|  
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Oui|  
|[MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Oui|  
|[MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Oui|  
|[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Oui|  
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|Oui|  
|[Ouvrir](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Oui|  
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Oui|  
|[Resync](../../../ado/reference/ado-api/resync-method.md)|Oui|  
|[Prise en charge](../../../ado/reference/ado-api/supports-method.md)|Oui|  
|[Update](../../../ado/reference/ado-api/update-method.md)|Non|  
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|Non|  
  
 Pour plus d’informations sur ADSI et les caractéristiques du fournisseur, reportez-vous à la documentation d’Active Directory Service Interfaces, ou visitez la page Web ADSI.  
  
## <a name="see-also"></a>Voir aussi  
 [CommandType, propriété (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)   
 [ConnectionString, propriété (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md)   
 [Collection de propriétés (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Fournisseur, propriété (ADO)](../../../ado/reference/ado-api/provider-property-ado.md)   
 [Objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Supports, méthode](../../../ado/reference/ado-api/supports-method.md)
