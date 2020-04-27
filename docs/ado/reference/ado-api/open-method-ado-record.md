---
title: Open, méthode (ADO record) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_Open
- _Record::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: ab79a623-88a9-40b6-a017-a658bf19b778
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97c7f1c143c83dd35ca5ff17e9776d79fb734ff9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917922"
---
# <a name="open-method-ado-record"></a>Open, méthode (objet Record ADO)
Ouvre un objet [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) existant ou crée un nouvel élément représenté par l' **enregistrement**, tel qu’un fichier ou un répertoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Open Source, ActiveConnection, Mode, CreateOptions, Options, UserName, Password  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Source*  
 Facultatif. **Variante** qui peut représenter l’URL de l’entité à représenter par cet objet **Record** , une **commande**, un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) ouvert ou un autre objet **Record** , une chaîne qui contient une instruction SQL SELECT ou un nom de table.  
  
 *ActiveConnection*  
 Facultatif. **Variant** qui représente la chaîne de connexion ou l’objet de [connexion](../../../ado/reference/ado-api/connection-object-ado.md) ouvert.  
  
 *Mode*  
 Facultatif. Valeur [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md) qui spécifie le mode d’accès pour l’objet **enregistrement** obtenu. La valeur par défaut est **adModeUnknown**.  
  
 *CreateOptions*  
 Facultatif. Valeur de [RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md) qui spécifie si un fichier ou un répertoire existant doit être ouvert ou si un nouveau fichier ou répertoire doit être créé. La valeur par défaut est **adFailIfNotExists**. Si la valeur par défaut est définie, le mode d’accès est obtenu à partir de la propriété [mode](../../../ado/reference/ado-api/mode-property-ado.md) . Ce paramètre est ignoré lorsque le paramètre *source* ne contient pas d’URL.  
  
 *Options*  
 Facultatif. Valeur de [RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md) qui spécifie les options d’ouverture de l' **enregistrement**. La valeur par défaut est **adOpenRecordUnspecified**. Ces valeurs peuvent être combinées.  
  
 *Nom d’utilisateur*  
 Facultatif. Valeur de **chaîne** qui contient l’ID d’utilisateur qui, s’il est requis, autorise l’accès à la *source*.  
  
 *Mot de passe*  
 Facultatif. Valeur de **chaîne** qui contient le mot de passe qui, le cas échéant, vérifie le *nom d’utilisateur*.  
  
## <a name="remarks"></a>Notes  
 La *source* peut être :  
  
-   URL. Si le protocole de l’URL est http, le fournisseur Internet est appelé par défaut. Si l’URL pointe vers un nœud qui contient un script exécutable (tel qu’un. ASP), un **enregistrement** qui contient la source à la place du contenu exécuté est ouvert par défaut. Utilisez l’argument *options* pour modifier ce comportement.  
  
-   Objet **enregistrement** . Un objet **Record** ouvert à partir d’un autre **enregistrement** clone l’objet **enregistrement** d’origine.  
  
-   Objet **Command** . L’objet **Record** ouvert représente la ligne unique retournée par l’exécution de la **commande**. Si les résultats contiennent plusieurs lignes, le contenu de la première ligne est placé dans l’enregistrement et une erreur peut être ajoutée à la collection d' **Erreurs** .  
  
-   Instruction SQL SELECT. L’objet **Record** ouvert représente la ligne unique retournée en exécutant le contenu de la chaîne. Si les résultats contiennent plusieurs lignes, le contenu de la première ligne est placé dans l’enregistrement et une erreur peut être ajoutée à la collection d' **Erreurs** .  
  
-   Nom de la table.  
  
 Si l’objet **Record** représente une entité qui n’est pas accessible à l’aide d’une URL (par exemple, une ligne d’un **jeu d’enregistrements** dérivé d’une base de données), les valeurs de la propriété [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md) et du champ accessible avec la constante **adRecordURL** sont null.  
  
> [!NOTE]
>  Les URL utilisant le schéma http appellera automatiquement le [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Pour plus d’informations, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Open, méthode (connexion ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open, méthode (objet Stream ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [OpenSchema, méthode](../../../ado/reference/ado-api/openschema-method.md)
