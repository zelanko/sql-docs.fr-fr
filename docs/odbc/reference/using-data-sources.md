---
title: À l’aide de Sources de données | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], about data sources
ms.assetid: d5550619-22b2-4b16-bd08-fbabb6554c40
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c898cb5cd8c9998d9126ec468a2b43587e2e279a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47728107"
---
# <a name="using-data-sources"></a>Utilisation des sources de données
Sources de données sont généralement créés par l’utilisateur final ou un technicien avec un programme appelé le *administrateur ODBC*. L’administrateur ODBC invite l’utilisateur pour le pilote à utiliser, puis appelle ce pilote. Le pilote affiche une boîte de dialogue qui demande les informations que nécessaires pour se connecter à la source de données. Une fois que l’utilisateur entre les informations, le pilote stocke sur le système.  
  
 Une version ultérieure, l’application appelle le Gestionnaire de pilotes et le transmet le nom d’une source de données machine ou le chemin d’accès d’un fichier contenant une source de données de fichier. Quand il est passé à un nom de source de données machine, le Gestionnaire de pilotes recherche dans le système pour rechercher le pilote utilisé par la source de données. Ensuite, il charge le pilote et lui passe le nom de source de données. Le pilote utilise le nom de source de données pour trouver les informations que nécessaires pour se connecter à la source de données. Enfin, il se connecte à la source de données, généralement en invitant l’utilisateur pour un ID utilisateur et le mot de passe, qui ne sont généralement pas stockées.  
  
 Quand il est passé à une source de données de fichier, le Gestionnaire de pilotes ouvre le fichier et charge le pilote spécifié. Si le fichier contient également une chaîne de connexion, il transmet au pilote. En utilisant les informations dans la chaîne de connexion, le pilote se connecte à la source de données. Si aucune chaîne de connexion a été passé, le pilote invite généralement l’utilisateur pour les informations nécessaires.
