---
title: Incitant l’utilisateur à obtenir des informations de connexion ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to data source [ODBC], SqlConnect
- connecting to driver [ODBC], prompting user for information
- connecting to driver [ODBC], SQLConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SqlDriverConnect
- SQLConnect function [ODBC], prompting user for connection information
- connecting to data source [ODBC], prompting user for information
- prompting user for connection information [ODBC]
- SQLDriverConnect function [ODBC], prompting user for connection information
ms.assetid: da98e9b9-a4ac-4a9d-bae6-e9252b1fe1e5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9b0f120a1076f14f5e67d506e52a446e0a3d4713
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282082"
---
# <a name="prompting-the-user-for-connection-information"></a>Demande des informations de connexion à l’utilisateur
Si l’application utilise **SQLConnect** et doit inciter l’utilisateur à toute information de connexion, comme un nom d’utilisateur et un mot de passe, il doit le faire lui-même. Bien que cela permette à l’application de contrôler son « look and feel », elle pourrait forcer l’application à contenir du code spécifique au conducteur. Cela se produit lorsque l’application doit inciter l’utilisateur à obtenir des informations de connexion spécifiques au conducteur. Cela présente une situation impossible pour les applications génériques, qui sont conçus pour travailler avec tous les conducteurs, y compris les conducteurs qui n’existent pas lorsque l’application est écrite.  
  
 **SQLDriverConnect** peut inciter l’utilisateur à obtenir des informations de connexion. Par exemple, le programme personnalisé mentionné précédemment pourrait passer la chaîne de connexion suivante à **SQLDriverConnect**:  
  
```  
DSN=XYZ Corp;  
```  
  
 Le conducteur peut alors afficher une boîte de dialogue qui invite pour les identifiants et mots de passe de l’utilisateur, similaire à l’illustration suivante.  
  
 ![Boîte de dialogue qui demande l'ID d'utilisateur et le mot de passe](../../../odbc/reference/develop-app/media/pr18.gif "pr18")  
  
 Que le conducteur peut inciter à des informations de connexion est particulièrement utile aux applications génériques et verticales. Ces applications ne doivent pas contenir d’informations spécifiques au conducteur, et le fait d’inviter le conducteur à obtenir les renseignements dont il a besoin permet de ne pas l’appliquer. Ceci est montré par les deux exemples précédents. Lorsque la demande n’a transmis que le nom de source de données au conducteur, l’application ne contenait aucune information spécifique au conducteur et n’était donc pas liée à un conducteur en particulier. Lorsque la demande a passé une chaîne de connexion complète au conducteur, elle était liée au conducteur qui pouvait interpréter cette chaîne.  
  
 Une application générique peut aller plus loin et ne même pas spécifier une source de données. Lorsque **SQLDriverConnect** reçoit une chaîne de connexion vide, le Driver Manager affiche la boîte de dialogue suivante.  
  
 ![Boîte de dialogue Sélectionner une source de données](../../../odbc/reference/develop-app/media/ch06a.gif "CH06A")  
  
 Une fois que l’utilisateur sélectionne une source de données, le Driver Manager construit une chaîne de connexion spécifiant cette source de données et la transmet au pilote. Le conducteur peut alors inciter l’utilisateur à obtenir des informations supplémentaires dont il a besoin.  
  
 Les conditions dans lesquelles le conducteur invite l’utilisateur sont contrôlées par le drapeau *DriverCompletion;* il ya des options pour toujours inviter, prompt si nécessaire, ou jamais prompt. Pour une description complète de ce drapeau, consultez la description de la fonction [SQLDriverConnect.](../../../odbc/reference/syntax/sqldriverconnect-function.md)
