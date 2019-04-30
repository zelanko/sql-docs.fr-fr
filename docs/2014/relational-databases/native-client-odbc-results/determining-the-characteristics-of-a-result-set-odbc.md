---
title: Détermination des caractéristiques d’un résultat de jeu (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], characteristics
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- SQLDescribeCol function
- metadata [ODBC]
- SQLColAttribute function
- SQLNumResultCols function
ms.assetid: 90be414c-04b3-46c0-906b-ae7537989b7d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba96d6312710f16f70b296dcb17bc3d5f226ff19
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63200204"
---
# <a name="determining-the-characteristics-of-a-result-set-odbc"></a>Détermination des caractéristiques d'un jeu de résultats (ODBC)
  Les métadonnées sont des données qui décrivent d'autres données. Par exemple, les métadonnées d'un jeu de résultats décrivent les caractéristiques de ce dernier, notamment le nombre de colonnes du jeu de résultats, les types de données de ces colonnes, leurs noms, leur précision, et si elles autorisent les valeurs Null.  
  
 ODBC fournit des métadonnées aux applications via ses fonctions API de catalogue. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client implémente la plupart des fonctions de catalogue API ODBC en tant qu’appels correspondant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] procédure catalogue.  
  
 Les applications requièrent des métadonnées pour la plupart des opérations de jeu de résultats. Par exemple, l'application utilise le type de données d'une colonne pour déterminer le type de variable à lier à cette colonne. Elle utilise la longueur d'octet d'une colonne de type caractère pour déterminer l'espace nécessaire à l'affichage des données à partir de cette colonne. La façon dont une application détermine les métadonnées d'une colonne dépend du type de l'application.  
  
 Les applications verticales utilisent en général des tables prédéfinies et effectuent des opérations prédéfinies sur ces tables. Dans la mesure où les métadonnées du jeu de résultats de ces applications sont définies avant même l'écriture de l'application, et comme elles sont contrôlées par le développeur, elles peuvent être codées de manière irréversible dans l'application. Par exemple, si une colonne d'ID d'ordre est définie en tant qu'entier de 4 octets dans la source de données, l'application peut toujours lier un entier de 4 octets à cette colonne. Lorsque les métadonnées sont codées de manière irréversible dans l'application, une modification des tables utilisées par l'application implique en général une modification du code de l'application.  
  
 Dans les applications génériques, en particulier les applications qui prennent en charge les requêtes ad hoc, les métadonnées des jeux de résultats qu'elles créent sont en général inconnues jusqu'au moment de l'exécution.  
  
 Pour déterminer les caractéristiques d'un jeu de résultats, une application peut appeler :  
  
-   [SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) pour déterminer le nombre de colonnes une requête est retourné.  
  
-   [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) ou [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) pour décrire une colonne du jeu de résultats.  
  
 Une application bien conçue est écrite à partir de l'hypothèse selon laquelle le jeu de résultats est inconnu ; en outre, elle utilise les informations retournées par ces fonctions pour lier les colonnes dans le jeu de résultats. Une application peut appeler ces fonctions à tout moment, une fois qu'une instruction a été préparée ou exécutée. Toutefois, pour des performances optimales, une application doit appeler **SQLColAttribute**, **SQLDescribeCol**, et **SQLNumResultCols** après une instruction est exécutée.  
  
 Vous pouvez avoir plusieurs appels simultanés pour des métadonnées. Les procédures du catalogue système sous-jacentes aux implémentations des API de catalogue ODBC peuvent être appelées par le pilote ODBC pendant qu'il utilise des curseurs côté serveur statiques. Cela permet aux applications de traiter de manière simultanée plusieurs appels aux fonctions de catalogue ODBC.  
  
 Si une application utilise un jeu de métadonnées particulier à plusieurs reprises, elle peut tirer parti de la mise en cache des informations dans des variables privées lors de leur obtention initiale. Cela évite d'appeler ultérieurement les fonctions de catalogue ODBC pour obtenir les mêmes informations en obligeant le pilote à effectuer des allers-retours au serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des résultats &#40;ODBC&#41;](processing-results-odbc.md)  
  
  
