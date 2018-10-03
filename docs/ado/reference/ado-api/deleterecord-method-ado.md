---
title: DeleteRecord, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_DeleteRecord
- _Record::DeleteRecord
helpviewer_keywords:
- DeleteRecord method [ADO]
ms.assetid: 2726498c-dbd8-4266-983b-ae7d62c39142
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23c66eb3ca786df27f856539e8bba026d2b1ea71
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47674110"
---
# <a name="deleterecord-method-ado"></a>DeleteRecord, méthode (ADO)
Supprime une entité représentée par un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Record.DeleteRecord Source, Async  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Source*  
 Facultatif. Un **chaîne** valeur qui contient une URL identifiant l’entité (par exemple, le fichier ou le répertoire) à supprimer. Si *Source* est omis ou spécifie une chaîne vide, l’entité représentée par l’actuel [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) est supprimé. Si l’enregistrement est une collection ([RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md) de **adCollectionRecord**, par exemple un répertoire) tous les enfants (par exemple, les sous-répertoires) seront également supprimés.  
  
 *Async*  
 Facultatif. Un **booléenne** valeur qui, lorsque **True**, spécifie que l’opération de suppression est asynchrone.  
  
## <a name="remarks"></a>Notes  
 Opérations sur l’objet représenté par ce **enregistrement** peuvent échouer après l’exécution de cette méthode. Après avoir appelé **DeleteRecord**, le **enregistrement** doit être fermé, car le comportement de la **enregistrement** peut devenir imprévisible selon quand le fournisseur met à jour le **Enregistrement** avec la source de données.  
  
 Si cette **enregistrement** a été obtenu à partir d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), puis les résultats de cette opération seront répercutées immédiatement dans le **Recordset**. Actualiser le **Recordset** en fermant et en rouvrant ou en exécutant la **Recordset** [Requery](../../../ado/reference/ado-api/requery-method.md) (méthode), le [mise à jour](../../../ado/reference/ado-api/update-method.md) (méthode), ou [Resync](../../../ado/reference/ado-api/resync-method.md) (méthode).  
  
> [!NOTE]
>  URL à l’aide du modèle http appellent automatiquement le [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Pour plus d’informations, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DELETE, méthode (Collection de champs ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [DELETE, méthode (Collection de paramètres ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)
