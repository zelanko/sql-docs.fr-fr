---
title: OpenSchema, méthode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::OpenSchema
- Connection15::raw_OpenSchema
helpviewer_keywords:
- OpenSchema method [ADO]
ms.assetid: 850cf3ce-f18f-4e7c-8597-96c1dc504866
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b2080145e00c658288f9d34e3fa42ed335e0c1d9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931863"
---
# <a name="openschema-method"></a>OpenSchema, méthode
Obtient les informations de schéma de base de données du fournisseur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Set recordset = connection.OpenSchema(QueryType, Criteria, SchemaID)  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet qui contient les informations de schéma. Le **Recordset** s’ouvre comme un curseur statique en lecture seule. Le *QueryType* détermine les colonnes qui apparaissent dans le **Recordset**.  
  
#### <a name="parameters"></a>Paramètres  
 *QueryType*  
 N’importe quel [SchemaEnum](../../../ado/reference/ado-api/schemaenum.md) valeur qui représente le type de requête de schéma à exécuter.  
  
 *Critères*  
 Facultatif. Un tableau de contraintes de requête pour chaque *QueryType* option, comme indiqué dans [SchemaEnum](../../../ado/reference/ado-api/schemaenum.md).  
  
 *SchemaID*  
 Le GUID pour une requête de schéma de fournisseur non défini par la spécification OLE DB. Ce paramètre est obligatoire si *QueryType* a la valeur **adSchemaProviderSpecific**; sinon, il n’est pas utilisé.  
  
## <a name="remarks"></a>Notes  
 Le **OpenSchema** méthode renvoie des informations autodescriptives sur la source de données, telles que les tables figurant dans la source de données, les colonnes dans les tables, et les types de données pris en charge.  
  
 Le *QueryType* argument est un GUID qui indique les colonnes (schémas) retournés. La spécification OLE DB a une liste complète des schémas.  
  
 Le *critères* argument limite les résultats d’une requête de schéma. *Critères* spécifie un tableau de valeurs qui doivent apparaître dans un sous-ensemble de colonnes, appelées colonnes de contrainte, dans le résultat correspondant **Recordset**.  
  
 La constante **adSchemaProviderSpecific** est utilisé pour le *QueryType* argument si le fournisseur définit ses propres requêtes de schéma non standard en dehors de celles répertoriées précédemment. Lorsque cette constante est utilisée, le *si IDSchéma* argument est nécessaire pour transmettre le GUID de la requête de schéma à exécuter. Si *QueryType* a la valeur **adSchemaProviderSpecific** mais *si IDSchéma* n’est pas fourni, une erreur se produit.  
  
 Fournisseurs ne sont pas requis pour prendre en charge toutes les requêtes de schéma standard OLE DB. Plus précisément, uniquement **requêtes adSchemaTables**, **adSchemaColumns**, et **adSchemaProviderTypes** sont requis par la spécification OLE DB. Toutefois, le fournisseur n’est pas requis pour prendre en charge la *critères* contraintes répertoriés plus haut pour ces requêtes de schéma.  
  
> [!NOTE]
>  **Utilisation de Service de données à distance** le **OpenSchema** méthode n’est pas disponible sur une côté client [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet.  
  
> [!NOTE]
>  En Visual Basic, les colonnes qui ont un entier non signé de 4 octets (DBTYPE UI4) dans le **Recordset** retourné à partir de la **OpenSchema** méthode sur le **connexion** objet ne peut pas comparé à d’autres variables. Pour plus d’informations sur les types de données OLE DB, consultez [dans OLE DB (OLE DB), les Types de données](https://msdn.microsoft.com/6039292f-74e0-49b2-b133-17bc117ebf6a) et [annexe a : Types de données](https://msdn.microsoft.com/e3a0533a-2196-4eb0-a31e-92fe9556ada6) dans la référence du programmeur Microsoft OLE DB.  
  
> [!NOTE]
>  **Visual C /C++ utilisateurs** lorsque vous N'utilisez pas les curseurs côté client, récupération de la « ORDINAL_POSITION » d’un schéma de colonne dans ADO renvoie un variant de type VT_R8 dans MDAC 2.7, MDAC 2.8 et Windows Data Access Components (Windows DAC) 6.0, tandis que le type utilisé dans MDAC 2.6 était VT_I4. Les programmes écrits pour MDAC 2.6 qui recherchent uniquement pour une variante retourné de type que VT_I4 obtiendriez un zéro pour chaque ordinal si s’exécuter sous Windows DAC 6.0 MDAC 2.7 et MDAC 2.8 sans modification. Cette modification a été effectuée, car le type de données OLE DB retourne est DBTYPE_UI4, et dans le type VT_I4 signé ne comporte pas assez d’espace pour contenir toutes les valeurs possibles sans troncation éventuellement qui se produisent, causant ainsi une perte de données.  
  
## <a name="applies-to"></a>S'applique à  
 [Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [La méthode OpenSchema, exemple (VB)](../../../ado/reference/ado-api/openschema-method-example-vb.md)   
 [La méthode OpenSchema, exemple (VC ++)](../../../ado/reference/ado-api/openschema-method-example-vc.md)   
 [Open, méthode (objet Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open, méthode (objet Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open, méthode (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Annexe A : fournisseurs](../../../ado/guide/appendixes/appendix-a-providers.md)
