---
title: MoveRecord, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::MoveRecord
- _Record::raw_MoveRecord
helpviewer_keywords:
- MoveRecord method [ADO]
ms.assetid: 6d2807b0-b861-4583-bcaf-fb0b82e0f2d0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: fe9dc770f537b9b9f8b53461c30b890a4144a821
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66707349"
---
# <a name="moverecord-method-ado"></a>MoveRecord, méthode (ADO)
Déplace l’entité représentée par un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) vers un autre emplacement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Record.MoveRecord (Source, Destination, UserName, Password, Options, Async)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Source*  
 Facultatif. Un **chaîne** valeur qui contient une URL qui identifie le **enregistrement** à déplacer. Si *Source* est omis ou spécifie une chaîne vide, l’objet représenté par ce **enregistrement** est déplacé. Par exemple, si le **enregistrement** représente un fichier, le contenu du fichier est déplacés vers l’emplacement spécifié par *Destination*.  
  
 *Destination*  
 Facultatif. Un **chaîne** valeur qui contient une URL en spécifiant l’emplacement où *Source* sera déplacé.  
  
 *UserName*  
 Facultatif. Un **chaîne** valeur qui contient l’ID utilisateur, si nécessaire, autorise l’accès *Destination*.  
  
 *Mot de passe*  
 Facultatif. Un **chaîne** qui contient le mot de passe, si nécessaire, vérifie *nom d’utilisateur*.  
  
 *Options*  
 Facultatif. Un [MoveRecordOptionsEnum](../../../ado/reference/ado-api/moverecordoptionsenum.md) valeur dont la valeur par défaut est **adMoveUnspecified**. Spécifie le comportement de cette méthode.  
  
 *Async*  
 Facultatif. Un **booléenne** valeur qui, lorsque **True**, indique cette opération doit être asynchrone.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur de **chaîne**. En règle générale, la valeur de *Destination* est retourné. Toutefois, la valeur exacte retournée dépend du fournisseur.  
  
## <a name="remarks"></a>Notes  
 Les valeurs de *Source* et *Destination* ne doit pas être identiques ; sinon, une erreur d’exécution se produit. Au moins les noms de serveur, chemin d’accès et des ressources doivent être différents.  
  
 Pour les fichiers déplacés à l’aide du fournisseur de publication Internet, cette méthode met à jour tous les liens hypertexte dans les fichiers déplacés, sauf indication contraire par *Options*. Cette méthode échoue si *Destination* identifie un objet existant (par exemple, un fichier ou répertoire), sauf si **adMoveOverWrite** est spécifié.  
  
> [!NOTE]
>  Utilisez le **adMoveOverWrite** option judicieusement. Par exemple, la spécification de cette option lorsque vous déplacez un fichier dans un répertoire sera supprimer le répertoire et remplacez-le par le fichier.  
  
 Certains attributs de la **enregistrement** l’objet, tel que le [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md) propriété, ne sera pas mis à jour une fois cette opération terminée. Actualiser le **enregistrement** des propriétés de l’objet en fermant le **enregistrement**, puis rouvrir avec l’URL de l’emplacement où le fichier ou répertoire a été déplacé.  
  
 Si cette **enregistrement** a été obtenu à partir d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), le nouvel emplacement du fichier déplacé ou du répertoire est répercutée immédiatement dans le **Recordset**. Actualiser le **Recordset** en fermant et en rouvrant.  
  
> [!NOTE]
>  URL à l’aide du modèle http appellent automatiquement le [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Pour plus d’informations, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Move, méthode (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [MoveFirst, MoveLast, MoveNext et MovePrevious, méthodes (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [MoveFirst, MoveLast, MoveNext et MovePrevious, méthodes (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)
