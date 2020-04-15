---
title: Utilisation de sources de données (en anglais seulement) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286539"
---
# <a name="using-data-sources"></a>Utilisation des sources de données
Les sources de données sont généralement créées par l’utilisateur final ou un technicien avec un programme appelé *l’administrateur ODBC*. L’administrateur ODBC invite l’utilisateur pour le conducteur à utiliser, puis appelle ce pilote. Le conducteur affiche une boîte de dialogue qui demande les informations dont il a besoin pour se connecter à la source de données. Une fois que l’utilisateur entre l’information, le conducteur les stocke sur le système.  
  
 Plus tard, l’application appelle le Driver Manager et lui transmet le nom d’une source de données de la machine ou la trajectoire d’un fichier contenant une source de données de fichiers. Lorsqu’il a passé un nom de source de données de machine, le gestionnaire de conducteur recherche le système pour trouver le conducteur utilisé par la source de données. Il charge ensuite le conducteur et lui transmet le nom de source de données. Le pilote utilise le nom de source de données pour trouver les informations dont il a besoin pour se connecter à la source de données. Enfin, il se connecte à la source de données, incitant généralement l’utilisateur pour un identifiant d’utilisateur et mot de passe, qui ne sont généralement pas stockés.  
  
 Lorsqu’il a été transmis une source de données de fichiers, le gestionnaire de conducteur ouvre le fichier et charge le conducteur spécifié. Si le fichier contient également une chaîne de connexion, il transmet cela au conducteur. En utilisant les informations contenues dans la chaîne de connexion, le pilote se connecte à la source de données. Si aucune chaîne de connexion n’a été franchie, le conducteur invite généralement l’utilisateur à obtenir les informations nécessaires.
