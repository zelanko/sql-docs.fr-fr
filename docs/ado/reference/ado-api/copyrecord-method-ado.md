---
title: "CopyRecord, méthode (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Record::raw_CopyRecord
- _Record::CopyRecord
helpviewer_keywords: CopyRecord method [ADO]
ms.assetid: b9bcf272-3c74-479f-95dd-0229a32e98fc
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9459d144016deaaec593a8edd92bf5b518a8962b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="copyrecord-method-ado"></a>CopyRecord, méthode (ADO)
Copie une entité représentée par un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) vers un autre emplacement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Record.CopyRecord (Source, Destination, UserName, Password, Options, Async)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Source*  
 Ce paramètre est facultatif. A **chaîne** valeur qui contient une URL spécifiant l’entité à copier (par exemple, un fichier ou répertoire). Si *Source* est omis ou spécifie une chaîne vide, le fichier ou le répertoire représenté par les [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) seront copiés.  
  
 *Destination*  
 Ce paramètre est facultatif. A **chaîne** valeur qui contient une URL spécifiant l’emplacement où *Source* seront copiés.  
  
 *UserName*  
 Ce paramètre est facultatif. A **chaîne** valeur qui contient l’ID utilisateur, si nécessaire, autorise l’accès aux *Destination*.  
  
 *Mot de passe*  
 Ce paramètre est facultatif. A **chaîne** valeur qui contient le mot de passe, si nécessaire, vérifie *nom d’utilisateur*.  
  
 *Options*  
 Ce paramètre est facultatif. A [CopyRecordOptionsEnum](../../../ado/reference/ado-api/copyrecordoptionsenum.md) valeur qui a la valeur par défaut **adCopyUnspecified**. Spécifie le comportement de cette méthode.  
  
 *Async*  
 Ce paramètre est facultatif. A **booléenne** valeur lorsque **True**, indique que cette opération doit être asynchrone.  
  
## <a name="return-value"></a>Valeur retournée  
 A **chaîne** valeur qui retourne généralement la valeur de *Destination*. Toutefois, la valeur exacte retournée dépend du fournisseur.  
  
## <a name="remarks"></a>Notes  
 Les valeurs de *Source* et *Destination* ne doit pas être identiques ; sinon, une erreur d’exécution se produit. Au moins un des noms de serveur, chemin d’accès ou ressource doit être différent.  
  
 Tous les enfants (par exemple, les sous-répertoires) de *Source* sont copiés de manière récursive, à moins que **valeur adCopyNonRecursive** est spécifié. Dans une opération récursive, *Destination* ne doit pas être un sous-répertoire de *Source*; sinon, l’opération ne sera pas terminée.  
  
 Cette méthode échoue si *Destination* identifie une entité existante (par exemple, un fichier ou répertoire), sauf si **adCopyOverWrite** est spécifié.  
  
> [!IMPORTANT]
>  Utilisez le **adCopyOverWrite** option judicieusement. Par exemple, la spécification de cette option lors de la copie d’un fichier dans un répertoire sera *supprimer* le répertoire et le remplacer par le fichier.  
  
> [!NOTE]
>  URL à l’aide du modèle http appellent automatiquement le [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Pour plus d’informations, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
