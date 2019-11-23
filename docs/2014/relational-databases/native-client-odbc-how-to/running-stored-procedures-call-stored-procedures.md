---
title: Appeler des procédures stockées (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a960df20b7b07bffab900589ae4d520541d720c1
ms.sourcegitcommit: 82a1ad732fb31d5fa4368c6270185c3f99827c97
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688665"
---
# <a name="call-stored-procedures-odbc"></a>Appeler des procédures stockées (ODBC)
  Lorsqu’une instruction SQL appelle une procédure stockée à l’aide de la clause ODBC CALL Escape, le pilote Microsoft SQL Server envoie la procédure à SQL Server à l’aide du mécanisme d’appel de procédure stockée distante (RPC). Les demandes RPC, qui contournent une grande partie de l'analyse des instructions et du traitement des paramètres dans SQL Server, sont plus rapides que l'instruction Transact-SQL EXECUTE.  
  
 Pour obtenir un exemple d’application qui illustre cette fonctionnalité, consultez [traiter les codes de &#40;retour&#41;et les paramètres de sortie ODBC](running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
### <a name="to-run-a-procedure-as-an-rpc"></a>Pour exécuter une procédure en tant qu'appel RPC  
  
1.  Construisez une instruction SQL qui utilise la séquence d'échappement ODBC CALL. L'instruction utilise des marqueurs de paramètre pour chaque entrée, entrée/sortie et paramètre de sortie, et pour la valeur de retour de la procédure (le cas échéant) :  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  Appelez [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) pour chaque paramètre d'entrée, d'entrée/sortie et de sortie et pour la valeur de retour de la procédure (le cas échéant).  
  
3.  Exécutez l'instruction avec [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399).  
  
> [!NOTE]  
>  Si une application soumet une procédure à l'aide de la syntaxe Transact-SQL EXECUTE (par opposition à la séquence d'échappement ODBC CALL), le pilote ODBC de SQL Server passe l'appel de procédure à SQL Server en tant qu'instruction SQL et non en tant qu'appel RPC. Par ailleurs, les paramètres de sortie ne sont pas retournés si l'instruction Transact-SQL EXECUTE est utilisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques &#40;de procédures relatives à l’exécution de&#41; procédures stockées ODBC](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)   
 [Appels de procédure stockée par traitement par lot](../native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)   
 [Exécution de procédures stockées](../native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Appel d’une procédure stockée](../native-client-odbc-stored-procedures/calling-a-stored-procedure.md)   
 [Procédures](../native-client-odbc-queries/executing-statements/procedures.md)  
  
  
