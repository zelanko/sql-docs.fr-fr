---
title: "À l’aide de Sources de données | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data sources [ODBC], about data sources
ms.assetid: d5550619-22b2-4b16-bd08-fbabb6554c40
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: eb3e6adb6f563e49429c2e04239ce3170d96b9a4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="using-data-sources"></a>À l’aide de Sources de données
Sources de données sont généralement créées par l’utilisateur final ou un technicien avec un programme appelé le *administrateur ODBC*. L’administrateur ODBC invite l’utilisateur pour le pilote à utiliser, puis appelle ce pilote. Le pilote affiche une boîte de dialogue qui demande les informations que nécessaires pour se connecter à la source de données. Une fois que l’utilisateur entre les informations, le pilote stocke sur le système.  
  
 Une version ultérieure, l’application appelle le Gestionnaire de pilotes et transmet le nom d’une source de données d’ordinateur ou le chemin d’accès d’un fichier contenant une source de données de fichier. Lorsqu’il est passé à un nom de source de données machine, le Gestionnaire de pilotes recherche dans le système pour rechercher le pilote utilisé par la source de données. Ensuite, il charge le pilote et lui transmet le nom de source de données. Le pilote utilise le nom de source de données pour trouver les informations que nécessaires pour se connecter à la source de données. Enfin, il se connecte à la source de données, généralement solliciter l’utilisateur pour un ID utilisateur et le mot de passe, qui ne sont généralement pas stockées.  
  
 Lorsqu’il est passé à une source de données de fichier, le Gestionnaire de pilotes ouvre le fichier et charge le pilote spécifié. Si le fichier contient également une chaîne de connexion, il le transmet au pilote. En utilisant les informations dans la chaîne de connexion, le pilote se connecte à la source de données. Si aucune chaîne de connexion a été passé, le pilote invite généralement l’utilisateur pour les informations nécessaires.

