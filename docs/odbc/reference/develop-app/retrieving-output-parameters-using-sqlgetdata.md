---
title: Récupération des paramètres de sortie à l’aide de SQLGetData (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], retrieving output parameters
- output parameters [ODBC]
- retrieving output parameters [ODBC]
ms.assetid: 7a8c298a-2160-491d-a300-d36f45568d9c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c96a3f9fc81d081ce16fe8e75746aafe8962fd0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294589"
---
# <a name="retrieving-output-parameters-using-sqlgetdata"></a>Récupération des paramètres de sortie à l’aide de SQLGetData
Avant ODBC 3.8, une application ne pouvait récupérer que les paramètres de sortie d’une requête avec un tampon de sortie lié. Cependant, il est difficile d’allouer un tampon très grand lorsque la taille de la valeur du paramètre est très grande (par exemple, une grande image). ODBC 3.8 introduit une nouvelle façon de récupérer les paramètres de sortie dans les pièces. Une application peut désormais appeler **SQLGetData** avec un petit tampon plusieurs fois pour récupérer une grande valeur de paramètre. Ceci est similaire à la récupération de grandes données de colonne.  
  
 Pour lier un paramètre de sortie ou un paramètre d’entrée/sortie à récupérer en pièces, appelez **SQLBindParameter** avec l’argument *InputOutputType* réglé pour SQL_PARAM_OUTPUT_STREAM ou SQL_PARAM_INPUT_OUTPUT_STREAM. Avec SQL_PARAM_INPUT_OUTPUT_STREAM, une application peut utiliser **SQLPutData** pour entrer les données dans le paramètre, puis utiliser **SQLGetData** pour récupérer le paramètre de sortie. Les données d’entrée doivent être sous forme de données à l’exécution (DAE), en utilisant **SQLPutData** au lieu de les lier à un tampon préaffecté.  
  
 Cette fonctionnalité peut être utilisée par les applications ODBC 3.8 ou les applications ODBC 3.x et ODBC 2.x recompilées, et ces applications doivent avoir un pilote ODBC 3.8 qui prend en charge la récupération des paramètres de sortie à l’aide **de SQLGetData** et ODBC 3.8 Driver Manager. Pour plus d’informations sur la façon de permettre à une ancienne application d’utiliser de nouvelles fonctionnalités ODBC, voir [Compatibilité Matrix](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
## <a name="usage-example"></a>Exemple d'utilisation  
 Par exemple, envisagez d’exécuter une procédure stockée, **«CALL sp_f (?,?),** où les deux paramètres sont liés comme SQL_PARAM_OUTPUT_STREAM, et la procédure stockée ne renvoie aucun ensemble de résultats (plus tard dans ce sujet, vous trouverez un scénario plus complexe):  
  
1.  Pour chaque paramètre, appelez **SQLBindParameter** avec *inputOutputType* réglé pour SQL_PARAM_OUTPUT_STREAM et *ParameterValuePtr* réglé à un jeton, comme un numéro de paramètre, un pointeur de données, ou un pointeur à une structure que l’application utilise pour lier les paramètres d’entrée. Cet exemple utilisera le paramètre ordinaire comme jeton.  
  
2.  Exécutez la requête avec **SQLExecDirect** ou **SQLExecute**. SQL_PARAM_DATA_AVAILABLE sera retournée, ce qui indique qu’il existe des paramètres de sortie en continu disponibles pour la récupération.  
  
3.  Appelez **SQLParamData** pour obtenir le paramètre disponible pour la récupération. **SQLParamData** retournera SQL_PARAM_DATA_AVAILABLE avec le jeton du premier paramètre disponible, qui est situé dans **SQLBindParameter** (étape 1). Le jeton est retourné dans le tampon que le *ValuePtrPtr* pointe vers.  
  
4.  Appelez **SQLGetData** avec l’argument\_ *Col*_or*Param_Num* réglé sur le paramètre ordinaire pour récupérer les données du premier paramètre disponible. Si **SQLGetData** retourne SQL_SUCCESS_WITH_INFO et SQLState 01004 (données tronquées), et que le type est de longueur variable tant sur le client que sur le serveur, il y a plus de données à récupérer à partir du premier paramètre disponible. Vous pouvez continuer à appeler **SQLGetData** jusqu’à ce qu’il retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO avec un **SQLState**différent .  
  
5.  Répétez l’étape 3 et l’étape 4 pour récupérer le paramètre actuel.  
  
6.  Appelez **SQLParamData** à nouveau. S’il renvoie quelque chose sauf SQL_PARAM_DATA_AVAILABLE, il n’y a plus de données de paramètres en streaming à récupérer, et le code de retour sera le code de retour de la prochaine instruction qui est exécutée.  
  
7.  Appelez **SQLMoreResults** pour traiter la prochaine série de paramètres jusqu’à ce qu’il revienne SQL_NO_DATA. **SQLMoreResults** retournera SQL_NO_DATA dans cet exemple si l’attribut de déclaration SQL_ATTR_PARAMSET_SIZE a été réglé à 1. Dans le cas contraire, **SQLMoreResults** retournera SQL_PARAM_DATA_AVAILABLE pour indiquer qu’il existe des paramètres de sortie en streaming disponibles pour la prochaine série de paramètres à récupérer.  
  
 Semblable à un paramètre d’entrée DAE, le jeton utilisé dans l’argument *ParameterValuePtr* dans **SQLBindParameter** (étape 1) peut être un pointeur qui indique une structure de données d’application, qui contient l’ordinaire du paramètre et plus d’informations spécifiques à l’application, si nécessaire.  
  
 L’ordre des paramètres de sortie ou d’entrée/sortie retranchés est spécifique au conducteur et peut ne pas toujours être le même que l’ordre spécifié dans la requête.  
  
 Si l’application n’appelle pas **SQLGetData** à l’étape 4, la valeur du paramètre est écartée. De même, si la demande appelle **SQLParamData** avant que toute une valeur de paramètre ait été lue par **SQLGetData**, le reste de la valeur est écarté, et la demande peut traiter le paramètre suivant.  
  
 Si la demande appelle **SQLMoreResults** avant que tous les paramètres de sortie en streaming ne soient traités **(SQLParamData** retourne toujours SQL_PARAM_DATA_AVAILABLE), tous les paramètres restants sont écartés. De même, si la demande appelle **SQLMoreResults** avant que toute une valeur de paramètre ait été lue par **SQLGetData**, le reste de la valeur et tous les paramètres restants sont écartés, et l’application peut continuer à traiter l’ensemble de paramètres suivant.  
  
 Notez qu’une application peut spécifier le type de données C dans **SQLBindParameter** et **SQLGetData**. Le type de données C spécifié avec **SQLGetData** remplace le type de données C spécifié dans **SQLBindParameter**, à moins que le type de données C spécifié dans **SQLGetData** ne soit SQL_APD_TYPE.  
  
 Bien qu’un paramètre de sortie en streaming soit plus utile lorsque le type de données du paramètre de sortie est de type BLOB, cette fonctionnalité peut également être utilisée avec n’importe quel type de données. Les types de données pris en charge par les paramètres de sortie en continu sont spécifiés dans le pilote.  
  
 S’il y a SQL_PARAM_INPUT_OUTPUT_STREAM paramètres à traiter, **SQLExecute** ou **SQLExecDirect** retourneront SQL_NEED_DATA en premier. Une application peut appeler **SQLParamData** et **SQLPutData** pour envoyer des données de paramètres DAE. Lorsque tous les paramètres d’entrée DAE sont traités, **SQLParamData** renvoie SQL_PARAM_DATA_AVAILABLE pour indiquer que des paramètres de sortie en streaming sont disponibles.  
  
 Lorsqu’il y a des paramètres de sortie en continu et des paramètres de sortie consolidés à traiter, le conducteur détermine la commande de traitement des paramètres de sortie. Ainsi, si un paramètre de sortie est lié à un tampon (le paramètre **SQLBindParameter** *InputOutputType* est réglé pour SQL_PARAM_INPUT_OUTPUT ou SQL_PARAM_OUTPUT), le tampon peut ne pas être peuplé jusqu’à ce que **SQLParamData** retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO. Une demande ne doit lire un tampon consolidé qu’après le retour **de SQLParamData** SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO qui est après que tous les paramètres de sortie en streaming sont traités.  
  
 La source de données peut retourner un avertissement et un ensemble de résultats, en plus du paramètre de sortie en streaming. En général, les avertissements et les ensembles de résultats sont traités séparément d’un paramètre de sortie en streaming en appelant **SQLMoreResults**. Avertissements de processus et le résultat défini avant le traitement du paramètre de sortie en streaming.  
  
 Le tableau suivant décrit différents scénarios d’une seule commande envoyée au serveur, et comment l’application doit fonctionner.  
  
|Scénario|Valeur de retour de SQLExecute ou SQLExecDirect|Que faire maintenant ?|  
|--------------|---------------------------------------------------|---------------------|  
|Les données ne comprennent que les paramètres de sortie en streaming|SQL_PARAM_DATA_AVAILABLE|Utilisez **SQLParamData** et **SQLGetData** pour récupérer les paramètres de sortie en streaming.|  
|Les données comprennent un ensemble de résultats et des paramètres de sortie en streaming|SQL_SUCCESS|Récupérez le résultat réglé avec **SQLBindCol** et **SQLGetData**.<br /><br /> Appelez **SQLMoreResults** pour commencer à traiter les paramètres de sortie en continu. Il devrait revenir SQL_PARAM_DATA_AVAILABLE.<br /><br /> Utilisez **SQLParamData** et **SQLGetData** pour récupérer les paramètres de sortie en streaming.|  
|Les données comprennent un message d’avertissement et des paramètres de sortie en streaming|SQL_SUCCESS_WITH_INFO|Utilisez **SQLGetDiagRec** et **SQLGetDiagField** pour traiter les messages d’avertissement.<br /><br /> Appelez **SQLMoreResults** pour commencer à traiter les paramètres de sortie en continu. Il devrait revenir SQL_PARAM_DATA_AVAILABLE.<br /><br /> Utilisez **SQLParamData** et **SQLGetData** pour récupérer les paramètres de sortie en streaming.|  
|Les données comprennent un message d’avertissement, un ensemble de résultats et des paramètres de sortie en streaming|SQL_SUCCESS_WITH_INFO|Utilisez **SQLGetDiagRec** et **SQLGetDiagField** pour traiter les messages d’avertissement. Appelez ensuite **SQLMoreResults** pour commencer à traiter l’ensemble de résultats.<br /><br /> Récupérez un jeu de résultat avec **SQLBindCol** et **SQLGetData**.<br /><br /> Appelez **SQLMoreResults** pour commencer à traiter les paramètres de sortie en continu. **SQLMoreResults** devrait revenir SQL_PARAM_DATA_AVAILABLE.<br /><br /> Utilisez **SQLParamData** et **SQLGetData** pour récupérer les paramètres de sortie en streaming.|  
|Requête avec les paramètres d’entrée DAE, par exemple, un paramètre d’entrée/sortie en streaming (DAE)|SQL NEED_DATA|Appelez **SQLParamData** et **SQLPutData** pour envoyer des données de paramètres d’entrée DAE.<br /><br /> Une fois que tous les paramètres d’entrée DAE sont traités, **SQLParamData** peut retourner tout code de retour que **SQLExecute** et **SQLExecDirect** peuvent retourner. Les cas dans ce tableau peuvent alors être appliqués.<br /><br /> Si le code de retour est SQL_PARAM_DATA_AVAILABLE, des paramètres de sortie en streaming sont disponibles. Une application doit appeler **SQLParamData** à nouveau pour récupérer le jeton pour le paramètre de sortie en streaming, tel que décrit dans la première rangée de ce tableau.<br /><br /> Si le code de retour est SQL_SUCCESS, soit il y a un résultat réglé pour traiter ou le traitement est terminé.<br /><br /> Si le code de retour est SQL_SUCCESS_WITH_INFO, il y a des messages d’avertissement à traiter.|  
  
 Après **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** retourne SQL_PARAM_DATA_AVAILABLE, une erreur de séquence de fonction se traduira si une application appelle une fonction qui n’est pas dans la liste suivante:  
  
-   **SQLAllocHandle** / **SQLAllocHandleStd**  
  
-   **SQLDataSources** / **SQLDrivers**  
  
-   **SQLGetInfo** / **SQLGetFunctions**  
  
-   **SQLGetConnectAttr** / **SQLGetEnvAttr** / **SQLGetDescField** / **SQLGetDescRec**  
  
-   **SQLNumParams**  
  
-   **SQLDescribeParam**  
  
-   **SQLNativeSql**  
  
-   **SQLParamData**  
  
-   **SQLMoreResults**  
  
-   **SQLGetDiagField** / **SQLGetDiagRec**  
  
-   **SQLCancel**  
  
-   **SQLCancelHandle** (avec poignée de déclaration)  
  
-   **SQLFreeStmt** (avec Option SQL_CLOSE, SQL_DROP ou SQL_UNBIND)  
  
-   **SQLCloseCursor**  
  
-   **SQLDisconnect**  
  
-   **SQLFreeHandle** (avec HandleType et SQL_HANDLE_STMT)  
  
-   **SQLGetStmtAttr**  
  
 Les applications peuvent toujours utiliser **SQLSetDescField** ou **SQLSetDescRec** pour définir les informations contraignantes. La cartographie sur le terrain ne sera pas modifiée. Cependant, les champs à l’intérieur du descripteur pourraient retourner de nouvelles valeurs. Par exemple, SQL_DESC_PARAMETER_TYPE peuvent retourner SQL_PARAM_INPUT_OUTPUT_STREAM ou SQL_PARAM_OUTPUT_STREAM.  
  
## <a name="usage-scenario-retrieve-an-image-in-parts-from-a-result-set"></a>Scénario d’utilisation : Récupérez une image en pièces à partir d’un ensemble de résultats  
 **SQLGetData** peut être utilisé pour obtenir des données dans les pièces lorsqu’une procédure stockée renvoie un ensemble de résultats qui contient une rangée de métadonnées sur une image et l’image est retournée dans un grand paramètre de sortie.  
  
```  
// CREATE PROCEDURE SP_TestOutputPara  
//      @ID_of_picture   as int,  
//      @Picture         as varbinary(max) out  
// AS  
//     output the image data through streamed output parameter  
// GO  
BOOL displayPicture(SQLUINTEGER idOfPicture, SQLHSTMT hstmt) {  
   SQLLEN      lengthOfPicture;    // The actual length of the picture.  
   BYTE        smallBuffer[100];   // A very small buffer.  
   SQLRETURN   retcode, retcode2;  
  
   // Bind the first parameter (input parameter)  
   SQLBindParameter(  
         hstmt,  
         1,                         // The first parameter.   
         SQL_PARAM_INPUT,           // Input parameter: The ID_of_picture.  
         SQL_C_ULONG,               // The C Data Type.  
         SQL_INTEGER,               // The SQL Data Type.  
         0,                         // ColumnSize is ignored for integer.  
         0,                         // DecimalDigits is ignored for integer.  
         &idOfPicture,              // The Address of the buffer for the input parameter.  
         0,                         // BufferLength is ignored for integer.  
         NULL);                     // This is ignored for integer.  
  
   // Bind the streamed output parameter.  
   SQLBindParameter(  
         hstmt,   
         2,                         // The second parameter.  
         SQL_PARAM_OUTPUT_STREAM,   // A streamed output parameter.   
         SQL_C_BINARY,              // The C Data Type.    
         SQL_VARBINARY,             // The SQL Data Type.  
         0,                         // ColumnSize: The maximum size of varbinary(max).  
         0,                         // DecimalDigits is ignored for binary type.  
         (SQLPOINTER)2,             // ParameterValuePtr: An application-defined  
                                    // token (this will be returned from SQLParamData).  
                                    // In this example, we used the ordinal   
                                    // of the parameter.  
         0,                         // BufferLength is ignored for streamed output parameters.  
         &lengthOfPicture);         // StrLen_or_IndPtr: The status variable returned.   
  
   retcode = SQLPrepare(hstmt, L"{call SP_TestOutputPara(?, ?)}", SQL_NTS);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   retcode = SQLExecute(hstmt);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   // Assume that the retrieved picture exists.  Use SQLBindCol or SQLGetData to retrieve the result-set.  
  
   // Process the result set and move to the streamed output parameters.  
   retcode = SQLMoreResults( hstmt );  
  
   // SQLGetData retrieves and displays the picture in parts.  
   // The streamed output parameter is available.  
   while (retcode == SQL_PARAM_DATA_AVAILABLE) {  
      SQLPOINTER token;   // Output by SQLParamData.  
      SQLLEN cbLeft;      // #bytes remained  
      retcode = SQLParamData(hstmt, &token);   // returned token is 2 (according to the binding)  
      if ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
         // A do-while loop retrieves the picture in parts.  
         do {  
            retcode2 = SQLGetData(   
               hstmt,   
               (UWORD) token,          // the value of the token is the ordinal.   
               SQL_C_BINARY,           // The C-type.  
               smallBuffer,            // A small buffer.   
               sizeof(smallBuffer),    // The size of the buffer.  
               &cbLeft);               // How much data we can get.  
         }  
         while ( retcode2 == SQL_SUCCESS_WITH_INFO );  
      }  
   }  
  
   return TRUE;  
}  
```  
  
## <a name="usage-scenario-send-and-receive-a-large-object-as-a-streamed-inputoutput-parameter"></a>Scénario d’utilisation : Envoyer et recevoir un grand objet en tant que paramètre d’entrée/sortie en streaming  
 **SQLGetData** peut être utilisé pour obtenir et envoyer des données dans les pièces lorsqu’une procédure stockée passe un grand objet comme un paramètre d’entrée/sortie, en continuant la valeur vers et depuis la base de données. Vous n’avez pas à stocker toutes les données en mémoire.  
  
```  
// CREATE PROCEDURE SP_TestInOut  
//       @picture as varbinary(max) out  
// AS  
//    output the image data through output parameter   
// go  
  
BOOL displaySimilarPicture(BYTE* image, ULONG lengthOfImage, SQLHSTMT hstmt) {  
   BYTE smallBuffer[100];   // A very small buffer.  
   SQLRETURN retcode, retcode2;  
   SQLLEN statusOfPicture;  
  
   // First bind the parameters, before preparing the statement that binds the output streamed parameter.  
   SQLBindParameter(  
      hstmt,   
      1,                                 // The first parameter.  
      SQL_PARAM_INPUT_OUTPUT_STREAM,     // I/O-streamed parameter: The Picture.  
      SQL_C_BINARY,                      // The C Data Type.  
      SQL_VARBINARY,                     // The SQL Data Type.  
      0,                                 // ColumnSize: The maximum size of varbinary(max).  
      0,                                 // DecimalDigits is ignored.   
      (SQLPOINTER)1,                     // An application defined token.   
      0,                                 // BufferLength is ignored for streamed I/O parameters.  
      &statusOfPicture);                 // The status variable.  
  
   statusOfPicture = SQL_DATA_AT_EXEC;   // Input data in parts (DAE parameter at input).  
  
   retcode = SQLPrepare(hstmt, L"{call SP_TestInOut(?) }", SQL_NTS);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   // Execute the statement.  
   retcode = SQLExecute(hstmt);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   if ( retcode == SQL_NEED_DATA ) {  
      // Use SQLParamData to loop through DAE input parameters.  For  
      // each, use SQLPutData to send the data to database in parts.  
  
      // This example uses an I/O parameter with streamed output.  
      // Therefore, the last call to SQLParamData should return  
      // SQL_PARAM_DATA_AVAILABLE to indicate the end of the input phrase   
      // and report that a streamed output parameter is available.  
  
      // Assume retcode is set to the return value of the last call to  
      // SQLParamData, which is equal to SQL_PARAM_DATA_AVAILABLE.  
   }  
  
   // Start processing the streamed output parameters.  
   while ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
      SQLPOINTER token;   // Output by SQLParamData.  
      SQLLEN cbLeft;     // #bytes remained  
      retcode = SQLParamData(hstmt, &token);  
      if ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
         do {  
            retcode2 = SQLGetData(   
               hstmt,   
               (UWORD) token,          // the value of the token is the ordinal.   
               SQL_C_BINARY,           // The C-type.  
               smallBuffer,            // A small buffer.   
               sizeof(smallBuffer),    // The size of the buffer.  
               &cbLeft);               // How much data we can get.  
         }  
         while ( retcode2 == SQL_SUCCESS_WITH_INFO );  
      }  
   }   
  
   return TRUE;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres des instructions](../../../odbc/reference/develop-app/statement-parameters.md)
