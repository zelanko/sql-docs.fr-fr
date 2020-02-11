---
title: Codes d’erreur ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO], error codes
ms.assetid: 3aee61c7-a9b7-4596-b78e-5828a00d0281
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9efe0f39ce304501096d9dcc682a0ea5d5137ee7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926999"
---
# <a name="capture-ado-error-codes"></a>Capturer les codes d’erreur ADO
Outre les erreurs de fournisseur retournées dans les objets [Error](../../../ado/reference/ado-api/error-object.md) de la collection [Errors](../../../ado/reference/ado-api/errors-collection-ado.md) , ADO lui-même peut retourner des erreurs au mécanisme de gestion des exceptions de votre environnement d’exécution. Utilisez le mécanisme d’interception des erreurs de votre langage de programmation, tel que l’instruction **On Error** dans Microsoft® Visual Basic ou le bloc **try-catch** dans Microsoft Visual C++®, pour capturer les erreurs ADO.

 Pour obtenir la liste des codes d’erreur ADO, consultez [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md).

## <a name="see-also"></a>Voir aussi
 [Error Object](../../../ado/reference/ado-api/error-object.md) [, collection d’erreurs (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)
