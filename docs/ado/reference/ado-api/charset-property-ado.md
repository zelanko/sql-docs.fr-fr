---
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: da9e41d594890b399be975a9f1465a6bff50010a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698803"
---
# <a name="charset-property-ado"></a>Charset, propriété (ADO)
Indique le jeu de caractères dans lequel le contenu d’un texte [Stream](../../../ado/reference/ado-api/stream-object-ado.md) doit être traduite pour le stockage dans la mémoire tampon interne de la **Stream** objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **chaîne** qui spécifie le caractère de la valeur dans laquelle le contenu de la **Stream** sera traduit. La valeur par défaut est **Unicode**. Valeurs autorisées sont des chaînes classiques transmises via l’interface en tant que noms de jeu de caractères Internet (par exemple, « iso-8859-1 », « Windows-1252 » et ainsi de suite). Pour obtenir la liste des noms de jeu de caractères sont connus par un système, consultez les sous-clés de HKEY_CLASSES_ROOT\MIME\Database\Charset dans le Registre Windows.  
  
## <a name="remarks"></a>Notes  
 Dans un texte **Stream** de l’objet, les données de texte sont stockées dans le jeu de caractères spécifié par le **Charset** propriété. La valeur par défaut est Unicode. Le **Charset** propriété est utilisée pour la conversion de données entrant dans le **Stream** ou bientôt de la **Stream**. Par exemple, si le **Stream** contient des données de ISO-8859-1 et que les données sont copiées vers un BSTR, le **Stream** objet convertit les données au format Unicode. L’inverse est également vrai.  
  
 Pour une ouverture **Stream**, actuel [Position](../../../ado/reference/ado-api/position-property-ado.md) doit se trouver au début de la **Stream** (0) pour pouvoir définir **Charset**.  
  
 **Jeu de caractères** est utilisé uniquement avec le texte **Stream** objets ([Type](../../../ado/reference/ado-api/type-property-ado-stream.md) est **adTypeText**). Cette propriété est ignorée si **Type** est **adTypeBinary**.  
  
 Pour obtenir un exemple de code, consultez [étape 4 : Remplir la zone de texte détails](../../../ado/guide/data/step-4-populate-the-details-text-box.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
