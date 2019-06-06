---
title: Source, propriété (objet Record ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::Source
- _Record::PutRefSource
- _Record::GetSource
- _Record::put_Source
- _Record::putref_Source
- _Record::get_Source
helpviewer_keywords:
- Source property [ADO Record]
ms.assetid: 2c18279e-6f35-4af0-b12e-8f1543d9ed20
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9217658a645d731645b0c85a419ecf759b1fd3bb
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66711107"
---
# <a name="source-property-ado-record"></a>Source, propriété (objet Record ADO)
Indique la source de données ou l’objet représenté par le [enregistrement](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **Variant** valeur qui indique l’entité représentée par le **enregistrement**.  
  
## <a name="remarks"></a>Notes  
 Le **Source** propriété retourne le *Source* argument de la **enregistrement** objet [Open](../../../ado/reference/ado-api/open-method-ado-record.md) (méthode). Il peut contenir une chaîne d’URL absolue ou relative. Une URL absolue peut être utilisée sans la [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) propriété pour ouvrir directement le **enregistrement** objet. Implicite **connexion** objet est créé dans ce cas.  
  
 Le **Source** propriété peut également contenir une référence à un déjà ouverte **Recordset**, qui ouvre un **enregistrement** objet représentant la ligne actuelle dans le  **Jeu d’enregistrements**.  
  
 Le **Source** propriété peut également contenir une référence à un [commande](../../../ado/reference/ado-api/command-object-ado.md) object qui retourne une seule ligne de données à partir du fournisseur.  
  
 Si le **ActiveConnection** propriété est également définie, puis le **Source** propriété doit pointer vers un objet qui existe dans l’étendue de cette connexion. Par exemple, dans les espaces de noms structuré en arborescence, si le **Source** propriété contient une URL absolue, elle doit pointer vers un nœud à la portée du nœud identifié par l’URL dans la chaîne de connexion. Si le **Source** propriété contient une URL relative, puis il est validé dans le contexte défini par le **ActiveConnection** propriété.  
  
 Le **Source** propriété est en lecture/écriture lors de la **enregistrement** objet est fermé et est en lecture seule tandis que le **enregistrement** objet est ouvert.  
  
> [!NOTE]
>  URL à l’aide du modèle http appellent automatiquement le [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Pour plus d’informations, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Source, propriété (objet Error ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [Source, propriété (objet Recordset ADO)](../../../ado/reference/ado-api/source-property-ado-recordset.md)
