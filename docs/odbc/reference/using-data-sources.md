---
title: Utilisation des sources de données | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df9b09e4c5519e0fff44902bd83b8e3d92a67ca8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81286539"
---
# <a name="using-data-sources"></a>Utilisation des sources de données
Les sources de données sont généralement créées par l’utilisateur final ou un technicien avec un programme appelé *administrateur ODBC*. L’administrateur ODBC invite l’utilisateur à utiliser le pilote, puis appelle ce pilote. Le pilote affiche une boîte de dialogue qui demande les informations dont il a besoin pour se connecter à la source de données. Une fois que l’utilisateur a entré les informations, le pilote le stocke sur le système.  
  
 Plus tard, l’application appelle le gestionnaire de pilotes et lui transmet le nom d’une source de données d’ordinateur ou le chemin d’un fichier contenant une source de données de fichier. Lorsqu’il reçoit un nom de source de données machine, le gestionnaire de pilotes recherche le pilote utilisé par la source de données dans le système. Il charge ensuite le pilote et lui transmet le nom de la source de données. Le pilote utilise le nom de la source de données pour trouver les informations dont il a besoin pour se connecter à la source de données. Enfin, il se connecte à la source de données, en général invitant l’utilisateur à entrer un ID d’utilisateur et un mot de passe, qui ne sont généralement pas stockés.  
  
 Lorsqu’il reçoit une source de données de fichier, le gestionnaire de pilotes ouvre le fichier et charge le pilote spécifié. Si le fichier contient également une chaîne de connexion, il le transmet au pilote. À l’aide des informations contenues dans la chaîne de connexion, le pilote se connecte à la source de données. Si aucune chaîne de connexion n’a été transmise, le pilote invite généralement l’utilisateur à fournir les informations nécessaires.
