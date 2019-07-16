---
title: ParentRow, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction::put_ParentRow
- ADORecordConstruction::ParentRow
- ADORecordConstruction::putParentRow
helpviewer_keywords:
- ParentRow property [ADO]
ms.assetid: 5ea8029b-eda4-490b-ae84-2ad036fb582f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a81eb6ee58d942547a159728b9c3edf9a30f1ece
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67917673"
---
# <a name="parentrow-property-ado"></a>ParentRow, propriété (ADO)
Définit le conteneur d’OLE DB **ligne** de l’objet sur un **ADORecordConstruction** de l’objet, afin que le parent de la ligne est activé dans ADO **enregistrement** objet.  
  
 En écriture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT put_ParentRow([in] IUnknown* pParent);  
```  
  
## <a name="parameters"></a>Paramètres  
 *pParent*  
 Un conteneur d’une ligne.  
  
## <a name="return-values"></a>Valeurs de retour  
 Cette méthode de propriété renvoie les valeurs HRESULT standard, notamment S_OK et E_FAIL.  
  
## <a name="applies-to"></a>S'applique à  
 [ADORecordConstruction, interface](../../../ado/reference/ado-api/adorecordconstruction-interface.md)
