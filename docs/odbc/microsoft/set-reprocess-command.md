---
title: SET REPROCESS, commande | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET REPROCESS command [ODBC]
ms.assetid: b0708757-b1d7-42f3-8988-787f2a806b8b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 41877986d5d0e8afdfb30841860df360efd26da0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63159373"
---
# <a name="set-reprocess-command"></a>SET REPROCESS, commande
Spécifie combien de fois ou sur la manière de longs pour verrouiller un fichier ou un enregistrement après une tentative infructueuse de verrouillage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET REPROCESS TO nAttempts [SECONDS] | TO AUTOMATIC  
```  
  
## <a name="arguments"></a>Arguments  
 POUR *nAttempts*[secondes]  
 Spécifie le nombre de fois ou le nombre de secondes à tente de verrouiller un fichier ou un enregistrement après une initiale échoue. La valeur par défaut est 0 ; la valeur maximale est de 32 000.  
  
 SECONDES Spécifie que Visual FoxPro tente de verrouiller un fichier ou l’enregistrement de *nAttempts* secondes. Il est disponible uniquement lorsque *nAttempts* est supérieure à zéro.  
  
 Par exemple, si *nAttempts* est 30, Visual FoxPro tente de verrouiller un enregistrement ou fichier jusqu'à 30 fois. Si vous incluez également secondes (valeur RETRAITER à 30 secondes), Visual FoxPro tente en permanence de verrouiller un enregistrement ou un fichier pendant 30 secondes.  
  
 Si une routine ON ERROR est activée et si les tentatives par une commande de verrouillage de l’enregistrement ou le fichier échouent, la routine ON ERROR est exécutée. Toutefois, si une fonction tente du verrou, une routine ON ERROR n’est pas exécutée et la fonction retourne False (. F.).  
  
 Si une routine ON ERROR n’est pas en vigueur, une commande tente de verrouiller l’enregistrement ou le fichier et le verrou ne peut pas être placé, une erreur est générée. Si une fonction tente de placer le verrou, l’alerte n’est pas affichée et que la fonction retourne False (. F.).  
  
 Si *nAttempts* est 0 (la valeur par défaut) et vous émettez une commande ou une fonction qui tente de verrouiller un enregistrement ou un fichier, Visual FoxPro tente de verrouillage de l’enregistrement ou fichier indéfiniment. Si l’enregistrement ou le fichier devient disponible pour le verrouillage en attendant, le verrou est placé et le message système est désactivé. Si une fonction a tenté de placer le verrou, la fonction retourne la valeur True (. T.).  
  
 Si une routine ON ERROR est en vigueur et une commande tente de verrouiller l’enregistrement ou le fichier, la routine ON ERROR est prioritaire sur supplémentaires tente de verrouiller l’enregistrement ou le fichier. La routine ON ERROR est exécutée immédiatement. Visual FoxPro n’essaie pas d’enregistrement supplémentaire ou verrous de fichier et n’affiche pas le message système.  
  
 Si *nAttempts* est 1, Visual FoxPro tente de verrouillage de l’enregistrement ou fichier indéfiniment et une routine ON ERROR n’est pas exécutée.  
  
 Si un verrou a été placé par un autre utilisateur sur l’enregistrement ou de la tentative de verrouillage de fichier, vous devez attendre jusqu'à ce que l’utilisateur relâche le verrou.  
  
 EN MODE AUTOMATIQUE  
 Spécifie que Visual FoxPro tente de verrouillage de l’enregistrement ou fichier indéfiniment. (Retraitement de SET-2 est une commande équivalente).  
  
## <a name="remarks"></a>Notes  
 La première tentative de verrouillage d’un enregistrement ou un fichier n’est pas toujours réussie. Souvent, un enregistrement ou un fichier est verrouillé par un autre utilisateur sur le réseau. Définissez RETRAITER détermine si Visual FoxPro rend supplémentaires tente de verrouiller l’enregistrement ou un fichier lorsque la tentative initiale échoue. Vous pouvez spécifier combien de fois tentatives supplémentaires sont effectuées ou pour la durée pendant laquelle les tentatives sont effectuées. Une routine ON ERROR affecte verrou comment échoué tentatives sont gérées.
