---
title: Exécution directe | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC applications, statements
- direct execution [ODBC]
- SQLExecDirect function
- statements [ODBC], direct execution
ms.assetid: fa36e1af-ed98-4abc-97c1-c4cc5d227b29
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 2da711afac37f6c51719577cd3965dce7c114eed
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39555319"
---
# <a name="direct-execution"></a>Exécution directe
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  L'exécution directe est la méthode d'exécution d'une instruction la plus simple. Une application génère une chaîne de caractères contenant une [!INCLUDE[tsql](../../../includes/tsql-md.md)] instruction et la soumet pour exécution en utilisant le **SQLExecDirect** (fonction). Lorsque l'instruction atteint le serveur, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] la compile dans un plan d'exécution et exécute immédiatement ce plan.  
  
 L'exécution directe est communément utilisée par les applications qui génèrent et exécutent des instructions au moment de l'exécution et s'avère la méthode la plus efficace pour les instructions qui ne sont exécutées qu'une seule fois. Elle présente néanmoins un inconvénient avec de nombreuses bases de données dans le sens où l'instruction SQL doit être analysée et compilée chaque fois qu'elle est exécutée, ce qui représente une surcharge en cas d'exécution répétée de l'instruction.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] améliore considérablement les performances de l'exécution directe d'instructions fréquemment exécutées dans les environnements multi-utilisateurs. En outre, l'utilisation de SQLExecDirect avec des marqueurs de paramètres pour les instructions SQL fréquemment exécutées peut permettre d'approcher l'efficacité d'une exécution préparée.  
  
 Lors de la connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client utilise [sp_executesql](../../../relational-databases/system-stored-procedures/sp-executesql-transact-sql.md) pour transmettre l’instruction SQL ou le traitement spécifié sur **SQLExecDirect**. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] intègre une logique permettant de déterminer rapidement si une instruction SQL ou lot exécuté avec **sp_executesql** correspond à l’instruction ou le lot qui a généré un plan d’exécution qui existe déjà dans la mémoire. Si une correspondance est trouvée, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] réutilise simplement le plan existant au lieu de compiler un nouveau plan. Cela signifie que les instructions SQL exécutées avec fréquemment exécutées **SQLExecDirect** dans un système comportant de nombreux utilisateurs bénéficient de nombreux avantages de réutilisation des plans qui étaient réservées exclusivement aux procédures stockées dans les versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 La réutilisation de plans d'exécution ne présente des avantages que si plusieurs utilisateurs exécutent la même instruction ou le même lot SQL. Suivez les conventions de codage suivantes pour accroître la probabilité que les instructions SQL exécutées par différentes clients soient suffisamment semblables pour pouvoir réutiliser des plans d'exécution :  
  
-   N'incluez pas de constantes de données dans les instructions SQL, mais utilisez des marqueurs de paramètres liés à des variables de programme. Pour plus d’informations, consultez [à l’aide de paramètres d’instruction](../../../relational-databases/native-client-odbc-queries/using-statement-parameters.md).  
  
-   Utilisez des noms d'objets complets. Les plans d'exécution ne sont pas réutilisés si les noms d'objets ne sont pas qualifiés.  
  
-   Dans la mesure du possible, faites que les connexions d'application utilisent un ensemble commun d'options de connexion et d'instruction. Les plans d'exécution générés pour une connexion avec un jeu d'options (tel qu'ANSI_NULLS) ne sont pas réutilisés pour une connexion ayant un autre jeu d'options. Le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client et le fournisseur OLE DB de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client partagent les mêmes paramètres par défaut pour ces options.  
  
 Si toutes les instructions exécutées avec **SQLExecDirect** sont codées à l’aide de ces conventions, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut réutiliser les plans d’exécution lorsque l’occasion se présente.  
  
## <a name="see-also"></a>Voir aussi  
 [L’exécution d’instructions &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
