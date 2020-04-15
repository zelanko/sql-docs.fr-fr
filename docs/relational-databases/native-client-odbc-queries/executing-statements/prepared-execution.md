---
title: Exécution préparée (fr) Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- deferred statement preparation
- prepared execution [ODBC]
- SQLPrepare function
- ODBC applications, statements
- SQLExecute function
- statements [ODBC], prepared execution
ms.assetid: f3a9d32b-6cd7-4f0c-b38d-c8ccc4ee40c3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8265ed80028d5d8ac9696853a29474552f401f3e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297917"
---
# <a name="prepared-execution"></a>Exécution préparée
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  L'API ODBC définit l'exécution préparée comme un moyen de réduire la charge d'analyse et de compilation associée à l'exécution répétée d'une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)]. L'application génère une chaîne de caractères contenant une instruction SQL, puis l'exécute en deux étapes. Il appelle [SQLPrepare Fonction](https://go.microsoft.com/fwlink/?LinkId=59360) une fois pour avoir la déclaration [!INCLUDE[ssDE](../../../includes/ssde-md.md)]analysée et compilée dans un plan d’exécution par le . Il appelle ensuite **SQLExecute** pour chaque exécution du plan d’exécution préparé. Cela permet de réduire la charge d'analyse et de compilation pour chaque exécution. L'exécution préparée est couramment utilisée par les applications pour exécuter de manière répétée la même instruction SQL paramétrable.  
  
 Avec la plupart des bases de données, l'exécution préparée est plus rapide que l'exécution directe pour les instructions qui sont exécutées plus de trois ou quatre fois principalement du fait que l'instruction est compilée une seule fois, alors que les instructions exécutées directement sont compilées chaque fois qu'elles sont exécutées. L'exécution préparée peut également permettre de réduire le trafic réseau car le pilote peut envoyer un identificateur de plan d'exécution et les valeurs de paramètre, plutôt qu'une instruction SQL entière, à la source de données chaque fois que l'instruction est exécutée.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]réduit la différence de performances entre l’exécution directe et l’exécution préparée grâce à des algorithmes améliorés pour détecter et réutiliser les plans d’exécution de **SQLExecDirect**. Les avantages de l'exécution préparée en termes de performances s'étendent ainsi dans une certaine mesure aux instructions exécutées directement. Pour plus d’informations, voir [Exécution directe](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] proposent également la prise en charge native de l'exécution préparée. Un plan d’exécution est construit sur **SQLPrepare** et exécuté plus tard lorsque **SQLExecute** est appelé. Parce [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qu’il n’est pas nécessaire de construire des procédures stockées temporaires sur **SQLPrepare**, il n’y a pas de frais généraux supplémentaires sur les tables du système dans **tempdb**.  
  
 Pour des raisons de rendement, la préparation de l’instruction est reportée jusqu’à ce que **SQLExecute** soit appelé ou qu’une opération de métaproperty (comme [SQLDescribeCol](../../../relational-databases/native-client-odbc-api/sqldescribecol.md) ou [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md) dans ODBC) soit effectuée. Il s'agit du comportement par défaut. Toute erreur dans l'instruction en cours de préparée reste inconnue tant que l'instruction n'a pas été exécutée ou qu'une opération de métapropriété n'a pas été effectuée. La définition de l'attribut SQL_SOPT_SS_DEFER_PREPARE de l'instruction spécifique au pilote ODBC  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  Native Client sur  SQL_DP_OFF peut désactiver ce comportement par défaut.  
  
 En cas de préparation différée, appeler **SQLDescribeCol** ou **SQLDescribeParam** avant d’appeler **SQLExecute** génère un aller-retour supplémentaire sur le serveur. Sur **SQLDescribeCol**, le conducteur supprime la clause WHERE de la requête et l’envoie au serveur avec SET FMTONLY ON pour obtenir la description des colonnes dans le premier ensemble de résultat retourné par la requête. Sur **SQLDescribeParam**, le conducteur appelle le serveur pour obtenir une description des expressions ou des colonnes référencées par tous les marqueurs de paramètres dans la requête. Cette méthode présente également certaines restrictions, comme le fait qu'elle ne permette pas de résoudre les paramètres dans les sous-requêtes.  
  
 L’utilisation excessive de **SQLPrepare** avec le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] conducteur native De Client ODBC dégrade les performances, surtout lorsqu’il est connecté à des versions antérieures de SQL Server. L'exécution préparée ne doit pas être utilisée pour les instructions exécutées une seule fois. L'exécution préparée est plus lente que l'exécution directe en cas d'exécution unique d'une instruction car elle requiert un aller-retour réseau supplémentaire entre le client et le serveur. Sur les versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], elle génère également une procédure stockée temporaire.  
  
 Les instructions préparées ne peuvent pas être utilisées pour la création d'objets temporaires dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Certaines premières applications ODBC utilisaient **SQLPrepare** chaque fois que [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md) était utilisé. **SQLBindParameter** n’a pas besoin de l’utilisation de **SQLPrepare**, il peut être utilisé avec **SQLExecDirect**. Par exemple, utilisez **SQLExecDirect** avec **SQLBindParameter** pour récupérer le code de retour ou les paramètres de sortie d’une procédure stockée qui n’est exécuté qu’une seule fois. N’utilisez pas **SQLPrepare** avec **SQLBindParameter** à moins que la même déclaration ne soit exécutée plusieurs fois.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution des déclarations &#40;&#41;ODBC](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
