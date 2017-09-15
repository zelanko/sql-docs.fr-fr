---
title: "Jeu de caractères, propriété (ADO) | Documents Microsoft"
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
- _Stream::Charset
helpviewer_keywords:
- Charset property [ADO]
ms.assetid: e42507cb-9b46-4ce4-8191-2948eaf14ca2
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8c3f9568a04572718bb6b1a968a3bacae4520898
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="charset-property-ado"></a>Jeu de caractères, propriété (ADO)
Indique le jeu de caractères dans lequel le contenu d’un texte [flux](../../../ado/reference/ado-api/stream-object-ado.md) doivent être traduites pour le stockage dans la mémoire tampon interne de la **flux** objet.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **chaîne** qui indique le caractère de la valeur dans laquelle le contenu de la **flux** va être traduite. La valeur par défaut est **Unicode**. Les valeurs autorisées sont des chaînes classiques transmises via l’interface en tant que noms de jeu de caractères Internet (par exemple, « iso-8859-1 », « Windows-1252 » et ainsi de suite). Pour obtenir la liste des noms de jeu de caractères sont reconnues par un système, consultez les sous-clés de HKEY_CLASSES_ROOT\MIME\Database\Charset dans le Registre Windows.  
  
## <a name="remarks"></a>Notes  
 Dans un texte **flux** de l’objet, les données de texte sont stockées dans le jeu de caractères spécifié par le **Charset** propriété. La valeur par défaut est Unicode. Le **Charset** propriété est utilisée pour la conversion des données vers le **flux** ou venir de le **flux**. Par exemple, si le **flux** contient des données de ISO-8859-1 et que les données sont copiées dans un BSTR, la **flux** objet convertit les données au format Unicode. L’inverse est également vrai.  
  
 Pour que l’ouverture **flux**, actuel [Position](../../../ado/reference/ado-api/position-property-ado.md) doit se trouver au début de la **flux** (0) pour pouvoir définir **Charset**.  
  
 **Jeu de caractères** est utilisé qu’avec du texte **flux** objets ([Type](../../../ado/reference/ado-api/type-property-ado-stream.md) est **adTypeText**). Cette propriété est ignorée si **Type** est **adTypeBinary**.  
  
 Pour un exemple de code, consultez [étape 4 : remplir la zone de texte Details](../../../ado/guide/data/step-4-populate-the-details-text-box.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Objet de flux de données (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
