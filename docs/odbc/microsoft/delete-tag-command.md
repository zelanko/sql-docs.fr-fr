---
title: Commande de balise DELETE | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 576e7e10d9d6f5c7e8616f57bde2dfed05503eae
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68112071"
---
# <a name="delete-tag-command"></a>DELETE TAG, commande
Supprime une ou plusieurs balises à partir d’un fichier d’index composé (.cdx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DELETE TAG TagName1 [OF CDXFileName1]  
   [, TagName2 [OF CDXFileName2]] ...  
  Or   
DELETE TAG ALL [OF CDXFileName]  
```  
  
## <a name="arguments"></a>Arguments  
 *TagName1*OF *CDXFileName1*[, *TagName2*[OF *CDXFileName2*]]...  
 Spécifie une balise à supprimer à partir d’un fichier d’index composés. Vous pouvez supprimer plusieurs balises avec une balise à supprimer en incluant une liste de noms de balises séparées par des virgules. Si deux ou plusieurs balises portant le même nom existent dans les fichiers d’index ouvert, vous pouvez supprimer une balise à partir d’un fichier d’index spécifique en incluant de *CDXFileName*.  
  
 Tous les [OF *CDXFileName*]  
 Supprime toutes les balises à partir d’un fichier d’index composés. Si la table actuelle comporte un fichier d’index composés structurelle, toutes les balises sont supprimées du fichier d’index, le fichier d’index est supprimé à partir du disque et l’indicateur dans l’en-tête du tableau indiquant la présence d’un fichier d’index composés structurelle associé est supprimé. Utilisez tout avec OF *CDXFileName* pour supprimer toutes les balises d’un fichier ouvrir l’index composés autre que le fichier d’index composés structurel.  
  
## <a name="remarks"></a>Notes  
 Fichiers d’index composés, créés avec un INDEX, contiennent des balises correspondant aux entrées d’index. SUPPRIMER la balise est utilisée pour supprimer une ou plusieurs balises à partir de fichiers d’index composés ouvert. Vous pouvez supprimer uniquement des balises à partir des fichiers d’index composé ouverts dans la zone de travail en cours. Si vous supprimez toutes les balises à partir d’un fichier d’index composés, le fichier est supprimé à partir du disque.  
  
 Visual FoxPro recherche d’abord pour une balise dans le fichier d’index composés structurelle (si celui-ci est ouvert). Si la balise n’est pas dans le fichier d’index composés structurelle, Visual FoxPro recherche ensuite la balise dans les autres fichiers ouvrir l’index composés.  
  
## <a name="see-also"></a>Voir aussi  
 [INDEX, commande](../../odbc/microsoft/index-command.md)
