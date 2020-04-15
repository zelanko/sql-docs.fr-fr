---
title: Set REPROCESS Commande (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5a7eb5fd19ca538c4f25077926567011ae133e54
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300829"
---
# <a name="set-reprocess-command"></a>SET REPROCESS, commande
Précise combien de fois ou pour combien de temps pour verrouiller un fichier ou un enregistrement après une tentative de verrouillage infructueuse.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET REPROCESS TO nAttempts [SECONDS] | TO AUTOMATIC  
```  
  
## <a name="arguments"></a>Arguments  
 À *nAttempts*[SECONDS]  
 Spécifie le nombre de fois ou de nombre de secondes pour essayer de verrouiller un enregistrement ou un fichier après une première tentative infructueuse. La valeur par défaut est de 0; la valeur maximale est de 32 000.  
  
 SECONDS précise que Visual FoxPro tente de verrouiller un fichier ou un enregistrement pour les secondes *nAttempts.* Il n’est disponible que lorsque *nAttempts* est supérieur à zéro.  
  
 Par exemple, si *nAttempts* est de 30, Visual FoxPro tente de verrouiller un enregistrement ou de fichier jusqu’à 30 fois. Si vous incluez également SECONDS (SET REPROCESS TO 30 SECONDS), Visual FoxPro tente en permanence de verrouiller un enregistrement ou un fichier jusqu’à 30 secondes.  
  
 Si une routine ON ERROR est en vigueur et si les tentatives d’une commande pour verrouiller l’enregistrement ou le fichier sont infructueuses, la routine ON ERROR est exécutée. Toutefois, si une fonction tente le verrou, une routine ON ERROR n’est pas exécutée et la fonction renvoie faux (. F.).  
  
 Si une routine ON ERROR n’est pas en vigueur, qu’une commande tente de verrouiller l’enregistrement ou le fichier, et que le verrou ne peut pas être placé, une erreur est générée. Si une fonction tente de placer la serrure, l’alerte n’est pas affichée et la fonction renvoie faux (. F.).  
  
 Si *nAttempts* est 0 (la valeur par défaut) et que vous émetssez une commande ou une fonction qui tente de verrouiller un enregistrement ou un fichier, Visual FoxPro tente de verrouiller l’enregistrement ou le fichier indéfiniment. Si l’enregistrement ou le fichier devient disponible pour le verrouillage pendant que vous attendez, le verrou est placé et le message du système est effacé. Si une fonction a tenté de placer la serrure, la fonction renvoie True (. T.).  
  
 Si une routine ON ERROR est en vigueur et qu’une commande tente de verrouiller l’enregistrement ou le fichier, la routine ON ERROR prime sur d’autres tentatives de verrouillage de l’enregistrement ou du fichier. La routine ON ERROR est immédiatement exécutée. Visual FoxPro ne tente pas d’enregistrers supplémentaires ou de verrouillages de fichiers et n’affiche pas le message du système.  
  
 Si *nAttempts* est 1, Visual FoxPro tente de verrouiller l’enregistrement ou le fichier indéfiniment et une routine ON ERROR n’est pas exécutée.  
  
 Si un verrou a été placé par un autre utilisateur sur l’enregistrement ou le fichier que vous tentez de verrouiller, vous devez attendre que l’utilisateur libère le verrou.  
  
 À AUTOMATIQUE  
 Précise que Visual FoxPro tente de verrouiller l’enregistrement ou le fichier indéfiniment. (SET REPROCESS TO -2 est une commande équivalente.)  
  
## <a name="remarks"></a>Notes  
 La première tentative de verrouillage d’un enregistrement ou d’un fichier n’est pas toujours réussie. Fréquemment, un enregistrement ou un fichier est verrouillé par un autre utilisateur sur le réseau. SET REPROCESS détermine si Visual FoxPro fait d’autres tentatives pour verrouiller l’enregistrement ou le fichier lorsque la tentative initiale est infructueuse. Vous pouvez spécifier le nombre de tentatives supplémentaires ou pour combien de temps les tentatives sont faites. Une routine ON ERROR affecte la façon dont les tentatives de verrouillage infructueuses sont traitées.
