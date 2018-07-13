---
title: Procédures | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC]
- stored procedures [ODBC], about ODBC stored procedures
- ODBC applications, statements
- statements [ODBC], stored procedures
- ODBC applications, stored procedures
ms.assetid: c64d5f3a-376b-48ef-84f3-b6148ac8600a
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0dc145646ea93081301b20f8e04fb5840bed78a8
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37417268"
---
# <a name="procedures"></a>Procédures
  Une procédure stockée est un objet exécutable précompilé qui contient une ou plusieurs instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Les procédures stockées peuvent posséder des paramètres d'entrée et de sortie et peuvent également émettre un code de retour de type entier. Une application peut énumérer les procédures stockées disponibles en utilisant des fonctions de catalogue.  
  
 Les applications ODBC qui ciblent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] doivent utiliser uniquement l'exécution directe pour appeler une procédure stockée. Lorsque connecté aux versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client implémente [SQLPrepare, fonction](http://go.microsoft.com/fwlink/?LinkId=59360) en créant une procédure stockée temporaire, qui est ensuite appelée **SQLExecute** . Il ajoute les servitudes logicielles pour que **SQLPrepare** créer une procédure stockée temporaire qui appelle la procédure stockée cible plutôt que directement de l’exécution de la cible de la procédure stockée. Même lors d'une connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], la préparation d'un appel requiert une boucle réseau supplémentaire et l'établissement d'un plan d'exécution qui appelle simplement le plan d'exécution de procédure stockée.  
  
 Les applications ODBC doivent utiliser la syntaxe ODBC CALL lors de l'exécution d'une procédure stockée. Le pilote est optimisé pour utiliser un mécanisme d'appel de procédure distante pour appeler la procédure lorsque la syntaxe ODBC CALL est utilisée. Ce mécanisme est plus efficace que celui utilisé pour envoyer une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE au serveur.  
  
 Pour plus d’informations, consultez [en cours d’exécution des procédures stockées](../../native-client-odbc-stored-procedures/running-stored-procedures.md).  
  
## <a name="see-also"></a>Voir aussi  
 [L’exécution d’instructions &#40;ODBC&#41;](executing-statements-odbc.md)  
  
  
