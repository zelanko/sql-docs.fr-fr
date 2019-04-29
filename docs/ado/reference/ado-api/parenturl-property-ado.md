---
title: ParentURL, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::ParentURL
helpviewer_keywords:
- ParentURL property [ADO]
ms.assetid: 65120ce6-3900-4cd4-b322-3b9816d74737
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e67ac30883a7665368f6f46045ff61d9375b8cd1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63027867"
---
# <a name="parenturl-property-ado"></a>ParentURL, propriété (ADO)
Indique l’URL absolue qui pointe vers le parent [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) d’actuel **enregistrement** objet.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un **chaîne** valeur qui indique l’URL du parent **enregistrement**.  
  
## <a name="remarks"></a>Notes  
 Le **ParentURL** propriété dépend de la source utilisée pour ouvrir le **enregistrement** objet. Par exemple, le **enregistrement** peut être ouvert avec une source qui contient un nom de chemin d’accès relatif d’un répertoire référencé par le [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) propriété.  
  
 Supposons que « second » est un sous-dossier de sous « first ». Ouvrez le **enregistrement** objet à l’aide de la syntaxe suivante :  
  
```  
record.ActiveConnection = "https://first"  
record.Open "second"  
```  
  
 À présent, la valeur de `the` **ParentURL** propriété est `"https://first"`, la même en tant que **ActiveConnection**.  
  
 La source peut également être une URL absolue, telle que, `"https://first/second"`. Le **ParentURL** propriété est alors `"https://first"`, du niveau supérieur `"second"`.  
  
 Cette propriété peut être une valeur null si :  
  
-   Il n’existe aucun parent pour l’objet actuel ; par exemple, si le **enregistrement** objet représente la racine d’un répertoire.  
  
-   Le **enregistrement** objet représente une entité qui ne peut pas être spécifiée avec une URL.  
  
 Cette propriété est en lecture seule.  
  
> [!NOTE]
>  Cette propriété est uniquement prise en charge par les fournisseurs de source de document, telles que la [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Pour plus d’informations, consultez [enregistrements et champs spécifiques au fournisseur](../../../ado/guide/data/records-and-provider-supplied-fields.md).  
  
> [!NOTE]
>  URL à l’aide du modèle http appellent automatiquement le [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Pour plus d’informations, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
> [!NOTE]
>  Si l’enregistrement actuel contient un enregistrement de données à partir d’un ADO **Recordset**, l’accès à la **ParentURL** propriété provoque une erreur d’exécution, indiquant qu’aucune URL n’est possible.  
  
## <a name="applies-to"></a>S'applique à  
 [Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
