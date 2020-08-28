---
description: Capturer les codes d’erreur ADO
title: Codes d’erreur ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO], error codes
ms.assetid: 3aee61c7-a9b7-4596-b78e-5828a00d0281
author: rothja
ms.author: jroth
ms.openlocfilehash: aa933f7be33f564af3aaf2851f6ec32bd5b4c5d4
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991180"
---
# <a name="capture-ado-error-codes"></a>Capturer les codes d’erreur ADO
Outre les erreurs de fournisseur retournées dans les objets [Error](../../reference/ado-api/error-object.md) de la collection [Errors](../../reference/ado-api/errors-collection-ado.md) , ADO lui-même peut retourner des erreurs au mécanisme de gestion des exceptions de votre environnement d’exécution. Utilisez le mécanisme d’interception des erreurs de votre langage de programmation, tel que l’instruction **On Error** dans Microsoft® Visual Basic ou le bloc **try-catch** dans Microsoft Visual C++®, pour capturer les erreurs ADO.

 Pour obtenir la liste des codes d’erreur ADO, consultez [ErrorValueEnum](../../reference/ado-api/errorvalueenum.md).

## <a name="see-also"></a>Voir aussi
 [Error Object](../../reference/ado-api/error-object.md) [, collection d’erreurs (ADO)](../../reference/ado-api/errors-collection-ado.md)