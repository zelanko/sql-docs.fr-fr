---
title: Appeler des procédures stockées (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ce757524bd43c403e89aaa1ebf0461c8e31ff381
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51663408"
---
# <a name="running-stored-procedures---call-stored-procedures"></a>Exécution de procédures stockées - Appeler des procédures stockées
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge l'exécution des procédures stockées en tant que procédures stockées distantes. L'exécution d'une procédure stockée en tant que procédure stockée distante permet au pilote et au serveur d'optimiser les performances de l'exécution de la procédure.  
  
  Lorsqu'une instruction SQL appelle une procédure stockée à l'aide de la clause d'échappement ODBC CALL, le pilote Microsoft® SQL Server™ envoie la procédure à SQL Server à l'aide du mécanisme d'appel de procédure stockée distante (RPC). Les demandes RPC, qui contournent une grande partie de l'analyse des instructions et du traitement des paramètres dans SQL Server, sont plus rapides que l'instruction Transact-SQL EXECUTE.  
  
 Pour un exemple d’application qui illustre cette fonctionnalité, consultez [traiter des Codes de retour et les paramètres de sortie &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
### <a name="to-run-a-procedure-as-an-rpc"></a>Pour exécuter une procédure en tant qu'appel RPC  
  
1.  Construisez une instruction SQL qui utilise la séquence d'échappement ODBC CALL. L'instruction utilise des marqueurs de paramètre pour chaque entrée, entrée/sortie et paramètre de sortie, et pour la valeur de retour de la procédure (le cas échéant) :  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  Appelez [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) pour chaque paramètre d'entrée, d'entrée/sortie et de sortie et pour la valeur de retour de la procédure (le cas échéant).  
  
3.  Exécutez l'instruction avec [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399).  
  
> [!NOTE]  
>  Si une application soumet une procédure à l'aide de la syntaxe Transact-SQL EXECUTE (par opposition à la séquence d'échappement ODBC CALL), le pilote ODBC de SQL Server passe l'appel de procédure à SQL Server en tant qu'instruction SQL et non en tant qu'appel RPC. Par ailleurs, les paramètres de sortie ne sont pas retournés si l'instruction Transact-SQL EXECUTE est utilisée.  
  
## <a name="see-also"></a>Voir aussi  
  [Traitement par lot des appels de procédure stockée](../../relational-databases/native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)   
 [Exécution de procédures stockées](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Appel d’une procédure stockée](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md)   
 [Procédures](../../relational-databases/native-client-odbc-queries/executing-statements/procedures.md)  
  
  
