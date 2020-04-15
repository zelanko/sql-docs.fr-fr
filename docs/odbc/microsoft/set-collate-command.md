---
title: Set COLLATE Commande ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set collate command [ODBC]
ms.assetid: 00efbcd4-fea8-4061-86a5-82de413cb753
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4a9c1dfd59c00ad0ac0b7bd8b8f1cdfccc84d9b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300889"
---
# <a name="set-collate-command"></a>SET COLLATE, commande
Spécifie une séquence de collation pour les champs de caractères dans les opérations ultérieures d’indexation et de tri.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET COLLATE TO cSequenceName  
```  
  
## <a name="arguments"></a>Arguments  
 *cSequenceName*  
 Spécifie une séquence de collation. Les options de séquence de collation disponibles sont décrites dans le tableau suivant.  
  
|Options|Langage|  
|-------------|--------------|  
|Néerlandais|Néerlandais|  
|GENERAL|Anglais, Français, Allemand, Espagnol moderne, Portugais et autres langues d’Europe occidentale|  
|Allemand|Commande allemande de livre de téléphone (DIN)|  
|Islande|Islandais|  
|Machine|Machine (la séquence de collation par défaut pour les versions FoxPro antérieures)|  
|NORDAN (NORDAN)|Norvégien, Danois|  
|Espagnol|Espagnol traditionnel|  
|SWEFIN (SWEFIN)|Suédois, Finlandais|  
|UNIQWT|Poids unique|  
  
> [!NOTE]  
>  Lorsque vous spécifiez l’option SPANISH, *ch* est une seule lettre qui trie entre *c* et *d*, et *trie* entre *l* et *m*.  
  
 Si vous spécifiez une option de séquence de collation comme chaîne de caractère littérale, assurez-vous d’inclure l’option dans les guillemets :  
  
```  
SET COLLATE TO "SWEFIN"  
```  
  
 MACHINE est l’option de séquence de collation par défaut et est la séquence que les utilisateurs de Xbase connaissent. Les caractères sont commandés au fur et à mesure qu’ils apparaissent dans la page de code actuelle.  
  
 GENERAL peut être préférable pour les utilisateurs américains et d’Europe occidentale. Les caractères sont commandés au fur et à mesure qu’ils apparaissent dans la page de code actuelle. Dans les versions FoxPro plus tôt que 2,5, des index pourraient avoir été créés en utilisant les fonctions **UPPER**( ) ou **LOWER**( ) pour convertir les champs de caractères en un cas cohérent. Dans les versions FoxPro plus tard que 2.5, vous pouvez plutôt spécifier l’option de séquence de collation GENERAL et omettre la conversion **UPPER**() .  
  
 Si vous spécifiez une option de séquence de collation autre que MACHINE et si vous créez un fichier .idx, un .idx compact est toujours créé.  
  
 Utilisez SET («COLLATE») pour retourner la séquence de collation actuelle.  
  
 Vous pouvez spécifier une séquence de collecte pour une source de données en utilisant la [boîte de dialogue de configuration De FoxPro visuelle D’ODBC](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md) ou en utilisant le mot clé Collate dans votre chaîne de connexion avec [SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md). Ceci est identique à l’émission de la commande suivante :  
  
```  
SET COLLATE TO cSequenceName  
```  
  
## <a name="remarks"></a>Notes  
 SET COLLATE vous permet de commander des tables contenant des caractères accentués pour l’une des langues prises en charge. La modification du paramètre SET COLLATE n’affecte pas la séquence de collatation des index précédemment ouverts. Visual FoxPro maintient automatiquement les index existants, offrant la flexibilité de créer de nombreux types d’index différents, même pour le même domaine.  
  
 Par exemple, si un index est créé avec SET COLLATE réglé sur GENERAL et que le paramètre SET COLLATE est ensuite modifié en SPANISH, l’indice conserve la séquence de collation GENERAL.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration d’ODBC pour Visual FoxPro, boîte de dialogue](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
