---
description: Charset, propriété (ADO)
title: CharSet, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Charset
helpviewer_keywords:
- Charset property [ADO]
ms.assetid: e42507cb-9b46-4ce4-8191-2948eaf14ca2
author: rothja
ms.author: jroth
ms.openlocfilehash: 9682664c87db42920c2ae78f338103c1d8c13d64
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88451001"
---
# <a name="charset-property-ado"></a>Charset, propriété (ADO)
Indique le jeu de caractères dans lequel le contenu d’un [flux](../../../ado/reference/ado-api/stream-object-ado.md) de texte doit être traduit pour le stockage dans la mémoire tampon interne de l’objet de **flux** .  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **chaîne** qui spécifie le jeu de caractères dans lequel le contenu du **flux** sera traduit. La valeur par défaut est **Unicode**. Les valeurs autorisées sont des chaînes typiques transmises à l’interface en tant que noms de jeux de caractères Internet (par exemple, « ISO-8859-1 », « Windows-1252 », etc.). Pour obtenir la liste des noms de jeux de caractères connus par un système, consultez les sous-clés de HKEY_CLASSES_ROOT \MIME\Database\Charset dans le Registre Windows.  
  
## <a name="remarks"></a>Notes  
 Dans un objet de **flux** de texte, les données texte sont stockées dans le jeu de caractères spécifié par la propriété **charset** . La valeur par défaut est Unicode. La propriété **charset** est utilisée pour convertir des données entrant dans le **flux** ou sortant du **flux**. Par exemple, si le **flux** contient des données ISO-8859-1 et que celles-ci sont copiées dans un BSTR, l’objet de **flux** convertira les données au format Unicode. L’inverse est également vrai.  
  
 Pour un **flux**ouvert, la [position](../../../ado/reference/ado-api/position-property-ado.md) actuelle doit se trouver au début du **flux** (0) pour pouvoir définir **charset**.  
  
 **Charset** est utilisé uniquement avec des objets de **flux** de texte (le[type](../../../ado/reference/ado-api/type-property-ado-stream.md) est **adTypeText**). Cette propriété est ignorée si le **type** est **adTypeBinary**.  
  
 Pour obtenir un exemple de code, consultez [étape 4 : remplir la zone de texte détails](../../../ado/guide/data/step-4-populate-the-details-text-box.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
