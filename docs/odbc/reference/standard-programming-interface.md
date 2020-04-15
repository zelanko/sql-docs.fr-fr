---
title: Interface de programmation standard (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c7767f113d0f70569ce253f0200cd35cb83915a4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81279995"
---
# <a name="standard-programming-interface"></a>Interface de programmation standard
L’interface de programmation est peut-être le candidat le plus évident pour la normalisation. En fait, lors de l’élaboration d’ODBC, l’ANSI et l’ISO ont déjà fourni des normes pour les modules SQL et SQL intégrés. Bien qu’il n’existe pas de normes pour une base de données CLI, le SQL Access Group - un consortium industriel de fournisseurs de bases de données - envisageait d’en créer une; parties de l’ODBC sont devenues plus tard la base de leur travail.  
  
 L’une des exigences pour ODBC était qu’un binaire d’application unique devait fonctionner avec plusieurs DBMS. C’est pour cette raison qu’ODBC n’utilise pas de langage SQL ou module intégré. Bien que la langue dans les langues SQL et module intégrées soit normalisée, chacune est liée aux précompilateurs spécifiques à DBMS. Ainsi, les applications doivent être recompilées pour chaque DBMS et les binaires qui en résultent ne fonctionnent qu’avec un seul DBMS. Bien que cela soit acceptable pour les applications à faible volume trouvées dans les mondes du mini-ordinateur et du mainframe, il est inacceptable dans le monde de l’informatique personnelle. Tout d’abord, c’est un cauchemar logistique de livrer plusieurs versions de logiciels à haut volume, enveloppés de rétrécissement aux clients; deuxièmement, les applications informatiques personnelles doivent souvent accéder simultanément à plusieurs DBMS.  
  
 D’autre part, une interface au niveau des appels peut être mise en œuvre par l’intermédiaire de bibliothèques, ou de pilotes de base de données, qui résident sur chaque machine locale; un pilote différent est nécessaire pour chaque DBMS. Étant donné que les systèmes d’exploitation modernes peuvent charger ces bibliothèques (telles que les bibliothèques de liaison dynamique sur le système d’exploitation Microsoft® Windows®) au moment de l’exécution, une seule application peut accéder aux données de différents DBMS sans recompilation et peut également accéder simultanément aux données de plusieurs bases de données. Au fur et à mesure que de nouveaux pilotes de base de données deviennent disponibles, les utilisateurs peuvent simplement les installer sur leurs ordinateurs sans avoir à modifier, recomposer ou reconnecter leurs applications de base de données. En outre, une interface de niveau d’appel était un bon candidat pour ODBC parce que Windows - la plate-forme pour laquelle ODBC a été initialement développé - déjà fait un usage intensif de ces bibliothèques.
