---
title: L’exécution de préparée | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- deferred statement preparation
- prepared execution [ODBC]
- SQLPrepare function
- ODBC applications, statements
- SQLExecute function
- statements [ODBC], prepared execution
ms.assetid: f3a9d32b-6cd7-4f0c-b38d-c8ccc4ee40c3
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 89ccf1c9fe8b3e69b55ec51be53dc6d3b63efdce
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154165"
---
# <a name="prepared-execution"></a>Exécution préparée
  L'API ODBC définit l'exécution préparée comme un moyen de réduire la charge d'analyse et de compilation associée à l'exécution répétée d'une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)]. L'application génère une chaîne de caractères contenant une instruction SQL, puis l'exécute en deux étapes. Il appelle [fonction SQLPrepare](http://go.microsoft.com/fwlink/?LinkId=59360) une fois pour que l’instruction soit analysée et compilée dans un plan d’exécution par le [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. Il appelle ensuite **SQLExecute** pour chaque exécution du plan d’exécution préparée. Cela permet de réduire la charge d'analyse et de compilation pour chaque exécution. L'exécution préparée est couramment utilisée par les applications pour exécuter de manière répétée la même instruction SQL paramétrable.  
  
 Avec la plupart des bases de données, l'exécution préparée est plus rapide que l'exécution directe pour les instructions qui sont exécutées plus de trois ou quatre fois principalement du fait que l'instruction est compilée une seule fois, alors que les instructions exécutées directement sont compilées chaque fois qu'elles sont exécutées. L'exécution préparée peut également permettre de réduire le trafic réseau car le pilote peut envoyer un identificateur de plan d'exécution et les valeurs de paramètre, plutôt qu'une instruction SQL entière, à la source de données chaque fois que l'instruction est exécutée.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] réduit la différence de performances entre les exécutions directe et préparée par le biais des algorithmes améliorés pour détecter et de réutiliser des plans d’exécution de **SQLExecDirect**. Les avantages de l'exécution préparée en termes de performances s'étendent ainsi dans une certaine mesure aux instructions exécutées directement. Pour plus d’informations, consultez [l’exécution directe](direct-execution.md).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] proposent également la prise en charge native de l'exécution préparée. Un plan d’exécution repose sur **SQLPrepare** puis exécuté lorsque **SQLExecute** est appelée. Étant donné que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] n’est pas requis pour générer des procédures stockées temporaires sur **SQLPrepare**, il n’existe aucune charge supplémentaire sur les tables système dans **tempdb**.  
  
 Pour des raisons de performances, la préparation de l’instruction est différée jusqu'à ce que **SQLExecute** est appelée ou une opération de métapropriété (tel que [SQLDescribeCol](../../native-client-odbc-api/sqldescribecol.md) ou [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md)dans ODBC) est effectuée. Il s'agit du comportement par défaut. Toute erreur dans l'instruction en cours de préparée reste inconnue tant que l'instruction n'a pas été exécutée ou qu'une opération de métapropriété n'a pas été effectuée. La définition de l'attribut SQL_SOPT_SS_DEFER_PREPARE de l'instruction spécifique au pilote ODBC  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  Native Client sur  SQL_DP_OFF peut désactiver ce comportement par défaut.  
  
 Dans le cas de différée préparer, appelant **SQLDescribeCol** ou **SQLDescribeParam** avant d’appeler **SQLExecute** génère un aller-retour supplémentaire vers le serveur. Sur **SQLDescribeCol**, le pilote supprime la clause WHERE de la requête et l’envoie au serveur avec SET FMTONLY ON pour obtenir la description des colonnes dans le premier jeu de résultats retourné par la requête. Sur **SQLDescribeParam**, le pilote appelle le serveur pour obtenir une description des expressions ou des colonnes référencées par les marqueurs de paramètre dans la requête. Cette méthode présente également certaines restrictions, comme le fait qu'elle ne permette pas de résoudre les paramètres dans les sous-requêtes.  
  
 L’utilisation excessive de **SQLPrepare** avec la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client dégrade les performances, surtout lorsque connecté aux versions antérieures de SQL Server. L'exécution préparée ne doit pas être utilisée pour les instructions exécutées une seule fois. L'exécution préparée est plus lente que l'exécution directe en cas d'exécution unique d'une instruction car elle requiert un aller-retour réseau supplémentaire entre le client et le serveur. Sur les versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], elle génère également une procédure stockée temporaire.  
  
 Les instructions préparées ne peuvent pas être utilisées pour la création d'objets temporaires dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Certaines anciennes applications ODBC utilisées **SQLPrepare** tout moment [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) a été utilisée. **SQLBindParameter** ne nécessite pas l’utilisation de **SQLPrepare**, il peut être utilisé avec **SQLExecDirect**. Par exemple, utilisez **SQLExecDirect** avec **SQLBindParameter** pour récupérer le code de retour ou paramètres à partir d’une procédure stockée est exécutée qu’une seule fois de sortie. N’utilisez pas **SQLPrepare** avec **SQLBindParameter** , sauf si l’instruction même doit être exécutée plusieurs fois.  
  
## <a name="see-also"></a>Voir aussi  
 [L’exécution d’instructions &#40;ODBC&#41;](executing-statements-odbc.md)  
  
  