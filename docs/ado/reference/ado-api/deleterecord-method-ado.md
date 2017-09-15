---
title: "DeleteRecord, méthode (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Record::raw_DeleteRecord
- _Record::DeleteRecord
helpviewer_keywords:
- DeleteRecord method [ADO]
ms.assetid: 2726498c-dbd8-4266-983b-ae7d62c39142
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a9ffdbf7024e513c22162c455e3a3378684e340e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="deleterecord-method-ado"></a>DeleteRecord, méthode (ADO)
Supprime une entité représentée par un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Record.DeleteRecord Source, Async  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Source*  
 Ce paramètre est facultatif. A **chaîne** valeur qui contient une URL qui identifie l’entité (par exemple, le fichier ou le répertoire) à supprimer. Si *Source* est omis ou spécifie une chaîne vide, l’entité représentée par le [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) est supprimé. Si l’enregistrement est une collection ([RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md) de **adCollectionRecord**, par exemple un répertoire) tous les enfants (par exemple, les sous-répertoires) seront également supprimés.  
  
 *Async*  
 Ce paramètre est facultatif. A **booléenne** valeur lorsque **True**, spécifie que l’opération de suppression est asynchrone.  
  
## <a name="remarks"></a>Notes  
 Opérations sur l’objet représenté par ce **enregistrement** peuvent échouer après l’exécution de cette méthode. Après avoir appelé **DeleteRecord**, le **enregistrement** doit être fermé, car le comportement de la **enregistrement** peut devenir imprévisible selon lorsque le fournisseur met à jour le **Enregistrement** avec la source de données.  
  
 Si cette **enregistrement** a été obtenu à partir d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), puis les résultats de cette opération seront répercutées immédiatement dans le **Recordset**. Actualiser le **Recordset** en fermant et en rouvrant ou en exécutant la **Recordset** [Requery](../../../ado/reference/ado-api/requery-method.md) (méthode), la [mise à jour](../../../ado/reference/ado-api/update-method.md) (méthode), ou [Resync](../../../ado/reference/ado-api/resync-method.md) (méthode).  
  
> [!NOTE]
>  URL à l’aide du modèle http appellent automatiquement le [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Pour plus d’informations, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Objet d’enregistrement (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DELETE, méthode (Collection de champs ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [DELETE, méthode (Collection de paramètres ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [DELETE, méthode (jeu d’enregistrements ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)
