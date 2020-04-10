---
title: Guide pratique pour spécifier la direction des paramètres avec le pilote SQLSRV | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedure support
ms.assetid: 1209eeca-df75-4283-96dc-714f39956b95
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 85a106a8e6a7f9afcac449b241b0255a16c51233
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80915925"
---
# <a name="how-to-specify-parameter-direction-using-the-sqlsrv-driver"></a>Procédure : spécifier la direction du paramètre à l’aide du pilote SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Cette rubrique décrit l’utilisation du pilote SQLSRV pour spécifier la direction du paramètre quand vous appelez une procédure stockée. La direction des paramètres est spécifiée lors de la construction d’un tableau de paramètres (étape 3) transmis à [sqlsrv_query](../../connect/php/sqlsrv-query.md) ou à [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md).  
  
### <a name="to-specify-parameter-direction"></a>Pour spécifier la direction du paramètre  
  
1.  Définissez une requête Transact-SQL qui appelle une procédure stockée. Utilisez des points d’interrogation (?) plutôt que les paramètres à passer à la procédure stockée. Par exemple, cette chaîne appelle une procédure stockée (UpdateVacationHours) qui accepte deux paramètres :  
  
    ```  
    $tsql = "{call UpdateVacationHours(?, ?)}";  
    ```  
  
    > [!NOTE]  
    > Appeler les procédures stockées à l’aide de la syntaxe canonique est la pratique recommandée. Pour plus d’informations sur la syntaxe canonique, consultez [Appel d’une procédure stockée](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md).  
  
2.  Initialisez ou mettez à jour les variables PHP qui correspondent aux espaces réservés dans la requête Transact-SQL. Par exemple, le code suivant initialise les deux paramètres de la procédure stockée UpdateVacationHours :  
  
    ```  
    $employeeId = 101;  
    $usedVacationHours = 8;  
    ```  
  
    > [!NOTE]  
    > Les variables initialisées ou mises à jour avec la valeur **null**, **DateTime**ou des types de flux ne peuvent pas être utilisées comme paramètres de sortie.  
  
3.  Utilisez vos variables PHP de l’étape 2 pour créer ou mettre à jour un tableau de valeurs de paramètre correspondant, dans l’ordre, aux espaces réservés de paramètre dans la chaîne Transact-SQL. Spécifiez la direction de chaque paramètre dans le tableau. La direction de chaque paramètre peut se déterminer de deux manières : par défaut (pour les paramètres d’entrée) ou à l’aide de constantes **SQLSRV_PARAM_\*** (pour les paramètres de sortie et les paramètres bidirectionnels). Par exemple, le code suivant spécifie le paramètre *$employeeId* comme paramètre d’entrée et le paramètre *$usedVacationHours* comme paramètre bidirectionnel :  
  
    ```  
    $params = array(  
                     array($employeeId, SQLSRV_PARAM_IN),  
                     array($usedVacationHours, SQLSRV_PARAM_INOUT)  
                    );  
    ```  
  
    Pour comprendre la syntaxe à utiliser pour spécifier la direction du paramètre en général, supposons que *$var1*, *$var2*et *$var3* correspondent respectivement au paramètre d’entrée, de sortie et bidirectionnel. Vous pouvez spécifier la direction du paramètre de l’une des manières suivantes :  
  
    -   Spécifiez implicitement le paramètre d’entrée, spécifiez explicitement le paramètre de sortie et spécifiez explicitement un paramètre bidirectionnel :  
  
        ```  
        array(   
               array($var1),  
               array($var2, SQLSRV_PARAM_OUT),  
               array($var3, SQLSRV_PARAM_INOUT)  
               );  
        ```  
  
    -   Spécifiez explicitement le paramètre d’entrée, spécifiez explicitement le paramètre de sortie et spécifiez explicitement un paramètre bidirectionnel :  
  
        ```  
        array(   
               array($var1, SQLSRV_PARAM_IN),  
               array($var2, SQLSRV_PARAM_OUT),  
               array($var3, SQLSRV_PARAM_INOUT)  
               );  
        ```  
  
4.  Exécutez la requête avec [sqlsrv_query](../../connect/php/sqlsrv-query.md) ou avec [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md) et [sqlsrv_execute](../../connect/php/sqlsrv-execute.md). Par exemple, le code suivant utilise la connexion *$conn* pour exécuter la requête *$tsql* avec les valeurs de paramètre spécifiées dans *$params*:  
  
    ```  
    sqlsrv_query($conn, $tsql, $params);  
    ```  
  
## <a name="see-also"></a>Voir aussi  
[Guide pratique pour récupérer des paramètres de sortie à l’aide du pilote SQLSRV](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)

[Guide pratique pour récupérer des paramètres d’entrée et de sortie à l’aide du pilote SQLSRV](../../connect/php/how-to-retrieve-input-and-output-parameters-using-the-sqlsrv-driver.md)  
  
