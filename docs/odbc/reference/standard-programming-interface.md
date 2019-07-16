---
title: Interface de programmation standard | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], programming interface
- programming interface standardization [ODBC]
ms.assetid: a2fa727e-51f2-4123-ae25-0ee28e611231
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a241ea92af6c1273039cc45daab232a1fbe763a3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68081837"
---
# <a name="standard-programming-interface"></a>Interface de programmation standard
L’interface de programmation est peut-être la plus évidente finale de normalisation. En fait, quand il était en cours de développement ODBC, ANSI et ISO déjà fourni normes pour embedded SQL et SQL modules. Bien qu’il existait aucune norme pour une base de données CLI, le groupe d’accès - un consortium d’entreprises de fournisseurs de base de données - SQL a été vous envisagez de créer un. parties d’ODBC ultérieurement est devenu la base de leur travail.  
  
 La configuration requise pour ODBC a qu’une seule application binaire devait fonctionner avec plusieurs systèmes SGBD. C’est pour cette raison que ODBC n’utilise pas embedded langages SQL ou un module. Bien que la langue dans les langues SQL et le module incorporés est normalisée, chacun est lié à precompilers de SGBD spécifiques. Par conséquent, les applications doivent être recompilées à chaque SGBD et les fichiers binaires qui en résulte fonctionnent uniquement avec un SGBD unique. Bien que cela soit acceptable pour les applications de faibles volumes trouvées dans les mondes ses et mainframe, il est interdit dans le monde de l’ordinateur personnel. Tout d’abord, il est un cauchemar logistique pour fournir plusieurs versions de logiciels volumineux, emballés à des clients ; en second lieu, applications de l’ordinateur personnel doivent souvent accéder simultanément à plusieurs systèmes SGBD.  
  
 En revanche, une interface de niveau d’appel peut être implémentée via des bibliothèques ou des pilotes de base de données, qui résident sur chaque ordinateur local ; un pilote différent est requis pour chaque SGBD. Étant donné que les systèmes d’exploitation modernes peuvent charger ces bibliothèques (telles que les bibliothèques de liens dynamiques sur le système d’exploitation Microsoft® Windows®) en cours d’exécution, une seule application peut accéder aux données à partir de différents SGBD sans recompilation et permettre également accéder aux données à partir de plusieurs bases de données simultanément. Comme les nouveaux pilotes de base de données deviennent disponibles, les utilisateurs peuvent installer uniquement ces sur leurs ordinateurs sans avoir à modifier, de recompiler ni de relier leurs applications de base de données. En outre, une interface de niveau d’appel a été un bon candidat pour ODBC, car Windows - la plateforme pour laquelle ODBC initialement développée - déjà ai beaucoup utilisé ces bibliothèques.
