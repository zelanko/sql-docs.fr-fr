---
title: Procédures ( Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC]
- stored procedures [ODBC], about ODBC stored procedures
- ODBC applications, statements
- statements [ODBC], stored procedures
- ODBC applications, stored procedures
ms.assetid: c64d5f3a-376b-48ef-84f3-b6148ac8600a
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 59d971f4d835470924874b0a08a648d36d98c0f9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297909"
---
# <a name="procedures"></a>Procédures
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Une procédure stockée est un objet exécutable précompilé qui contient une ou plusieurs instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Les procédures stockées peuvent posséder des paramètres d'entrée et de sortie et peuvent également émettre un code de retour de type entier. Une application peut énumérer les procédures stockées disponibles en utilisant des fonctions de catalogue.  
  
 Les applications ODBC qui ciblent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] doivent utiliser uniquement l'exécution directe pour appeler une procédure stockée. Lorsqu’il est connecté [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] des versions antérieures de , le conducteur native ODBC implémente [SQLPrepare Fonction](https://go.microsoft.com/fwlink/?LinkId=59360) en créant une procédure de stockage temporaire, qui est ensuite appelé sur **SQLExecute**. Il ajoute au-dessus de la tête pour que **SQLPrepare** crée une procédure stockée temporaire qui n’appelle que la procédure stockée par cible plutôt que l’exécution directe de la procédure stockée par cible. Même lors d'une connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], la préparation d'un appel requiert une boucle réseau supplémentaire et l'établissement d'un plan d'exécution qui appelle simplement le plan d'exécution de procédure stockée.  
  
 Les applications ODBC doivent utiliser la syntaxe ODBC CALL lors de l'exécution d'une procédure stockée. Le pilote est optimisé pour utiliser un mécanisme d'appel de procédure distante pour appeler la procédure lorsque la syntaxe ODBC CALL est utilisée. Ce mécanisme est plus efficace que celui utilisé pour envoyer une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE au serveur.  
  
 Pour plus d’informations, voir [Procédures stockées en cours d’exécution](../../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution des déclarations &#40;&#41;ODBC](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
