---
title: Gestion des erreurs dans Visual C++ | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- errors [ADO], Visual C++
- Visual C++ error handling [ADO]
ms.assetid: b7576f07-020a-45f7-9e79-b5756f33f7ab
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c584eda82a6a3f28b6eb78e1fd83046be31fe76
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="handling-errors-in-visual-c"></a>Gestion des erreurs dans Visual C++
Dans COM, la plupart des opérations renvoient un code de retour HRESULT qui indique si une fonction a réussi. La directive #import génère du code wrapper autour de chaque méthode « brut » ou une propriété et vérifie le HRESULT retourné. Si la valeur HRESULT indique un échec, le code wrapper génère une erreur COM en appelant _com_issue_errorex() avec le code de retour HRESULT en tant qu’argument. Objets d’erreur COM peuvent être interceptées dans un **try-catch** bloc. (Par souci d’efficacité, interceptez une référence à un objet _com_error.)  
  
 N’oubliez pas, il s’agit d’erreurs ADO : elles résultent de l’échec d’une opération ADO. Les erreurs renvoyées par le fournisseur sous-jacent apparaissent en tant que **erreur** des objets dans le **connexion** l’objet **erreurs** collection.  
  
 La directive #import crée uniquement des routines de gestion des erreurs pour les méthodes et propriétés déclarées dans le fichier .dll ADO. Toutefois, vous pouvez tirer parti de ce même mécanisme de gestion des erreurs en écrivant votre propre fonction inline ou macro la vérification des erreurs. Consultez la rubrique des Extensions Visual C++® pour obtenir des exemples.
