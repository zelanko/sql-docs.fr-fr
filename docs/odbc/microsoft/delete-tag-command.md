---
title: Delete TAG Commande (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DELETE TAG command [ODBC]
ms.assetid: 4f4e1362-a5f3-4b15-8a3c-d4e96605f221
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 97ca5abca7e70f5dffdae9bf14ce64429fd203d5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303540"
---
# <a name="delete-tag-command"></a>DELETE TAG, commande
Supprime une balise ou des balises d’un fichier d’index composé (.cdx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DELETE TAG TagName1 [OF CDXFileName1]  
   [, TagName2 [OF CDXFileName2]] ...  
  Or   
DELETE TAG ALL [OF CDXFileName]  
```  
  
## <a name="arguments"></a>Arguments  
 *TagName1 (en)* OF *CDXFileName1*[, *TagName2*[OF *CDXFileName2*]] ...  
 Spécifie une balise à supprimer d’un fichier d’index composé. Vous pouvez supprimer plusieurs balises avec un TAG DELETE en incluant une liste de noms d’étiquettes séparés par des virgules. Si deux balises ou plus du même nom existent dans les fichiers d’index ouverts, vous pouvez supprimer une balise d’un fichier index spécifique en incluant OF *CDXFileName*.  
  
 TOUS [DE *CDXFileName*]  
 Supprime chaque balise d’un fichier d’index composé. Si le tableau actuel dispose d’un fichier d’index composé structurel, toutes les balises sont supprimées du fichier index, le fichier indiciel est supprimé du disque, et le drapeau dans l’en-tête du tableau indiquant la présence d’un fichier d’index composé structurel associé est supprimé. Utilisez ALL with OF *CDXFileName* pour supprimer toutes les balises d’un fichier d’index composé ouvert autre que le fichier d’index composé structurel.  
  
## <a name="remarks"></a>Notes  
 Les fichiers index composés, créés avec INDEX, contiennent des balises correspondant aux entrées indiciels. DELETE TAG est utilisé pour supprimer une balise ou des balises des fichiers d’index composés ouverts. Vous ne pouvez supprimer que les balises des fichiers index composés ouverts dans la zone de travail actuelle. Si vous supprimez toutes les balises d’un fichier d’index composé, le fichier est supprimé du disque.  
  
 Visual FoxPro semble d’abord pour une étiquette dans le fichier d’index composé structurel (si l’on est ouvert). Si le tag n’est pas dans le fichier d’index composé structurel, Visual FoxPro recherche alors l’étiquette dans les autres fichiers d’index composé ouvert.  
  
## <a name="see-also"></a>Voir aussi  
 [INDEX, commande](../../odbc/microsoft/index-command.md)
