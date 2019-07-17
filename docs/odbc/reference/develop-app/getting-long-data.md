---
title: Obtention de données Long | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- long data [ODBC]
- fetches [ODBC], long data
- result sets [ODBC], fetching
- SQLGetData function [ODBC], getting long data
- retrieving long data [ODBC]
ms.assetid: 6ccb44bc-8695-4bad-91af-363ef22bdb85
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 49f0023f726dd4bb290ffba1018ce2608800dd90
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68216361"
---
# <a name="getting-long-data"></a>Obtention de données de type Long
Définir des SGBD *données de type long* comme tout caractère ou les données binaires sur une certaine taille, telles que 255 caractères. Ces données peuvent être assez petites pour être stocké dans une seule mémoire tampon, par exemple une description de partie de plusieurs caractères de milliers. Toutefois, il peut être trop long pour stocker en mémoire, telles que les documents de texte long ou des bitmaps. Étant donné que ces données ne peuvent pas être stockées dans une seule mémoire tampon, il est récupéré à partir du pilote dans des parties avec **SQLGetData** après les autres données de la ligne ont été extraites.  
  
> [!NOTE]  
>  Une application peut récupérer en fait de n’importe quel type de données avec **SQLGetData**, ne long pas seulement les données, même si uniquement des caractères et des données binaires peuvent être récupérées dans les parties. Toutefois, si les données sont suffisamment petites pour tenir dans une seule mémoire tampon, il est généralement inutile d’utiliser **SQLGetData**. Il est beaucoup plus facile de lier une mémoire tampon à la colonne et laisser le pilote de renvoyer les données de la mémoire tampon.  
  
 Pour récupérer des données de type long à partir d’une colonne, une application appelle d’abord **SQLFetchScroll** ou **SQLFetch** pour déplacer vers une ligne et extraire les données pour les colonnes liées. L’application appelle ensuite **SQLGetData**. **SQLGetData** a les mêmes arguments que **SQLBindCol**: un descripteur d’instruction ; un numéro de colonne ; le C type, l’adresse et octets longueur des données d’une variable d’application et l’adresse d’une mémoire tampon de longueur / d’indicateur. Les deux fonctions ont les mêmes arguments, car ils effectuent essentiellement la même tâche : À la fois, ils décrivent une variable d’application pour le pilote et spécifient que les données pour une colonne particulière doivent être renvoyées dans cette variable. Les principales différences sont que **SQLGetData** est appelée après qu’une ligne est extraite (et est parfois appelé *liaison tardive* pour cette raison) et que la liaison spécifiée par **SQLGetData**  uniquement pendant toute la durée de l’appel.  
  
 Ce qui concerne une colonne unique, **SQLGetData** se comporte comme **SQLFetch**: Il récupère les données pour la colonne, il convertit le type de la variable d’application et le renvoie dans cette variable. Il retourne également la longueur d’octet des données dans la mémoire tampon de longueur / d’indicateur. Pour plus d’informations sur la façon **SQLFetch** renvoie des données, consultez [l’extraction d’une ligne de données](../../../odbc/reference/develop-app/fetching-a-row-of-data.md).  
  
 **SQLGetData** diffère **SQLFetch** un aspect important. Si elle est appelée plusieurs fois de suite pour la même colonne, chaque appel retourne une partie successif des données. Chaque appel à l’exception du dernier appel retourne SQL_SUCCESS_WITH_INFO et SQLSTATE 01004 (chaîne de données droit tronqué) ; le dernier appel retourne SQL_SUCCESS. Voici comment **SQLGetData** est utilisée pour récupérer des données de type long dans les parties. Lorsqu’il n’existe aucune donnée supplémentaire à renvoyer, **SQLGetData** retourne SQL_NO_DATA. L’application est chargée de rassembler les données longues, ce qui peut signifier concaténant les parties des données. Chaque partie se termine par null ; l’application doit supprimer le caractère de fin de la valeur null si concaténant les parties. Récupération de données en parties est possible pour les signets de longueur variable, ainsi que pour d’autres données de type long. La valeur retournée dans la baisse de mémoire tampon de longueur / d’indicateur dans chaque appel par le nombre d’octets retournés dans l’appel précédent, bien qu’il est courant pour le pilote est impossible de découvrir la quantité de données disponibles et retourner une longueur d’octet de SQL_NO_TOTAL. Exemple :  
  
```  
// Declare a binary buffer to retrieve 5000 bytes of data at a time.  
SQLCHAR       BinaryPtr[5000];  
SQLUINTEGER   PartID;  
SQLINTEGER    PartIDInd, BinaryLenOrInd, NumBytes;  
SQLRETURN     rc;   
SQLHSTMT      hstmt;  
  
// Create a result set containing the ID and picture of each part.  
SQLExecDirect(hstmt, "SELECT PartID, Picture FROM Pictures", SQL_NTS);  
  
// Bind PartID to the PartID column.  
SQLBindCol(hstmt, 1, SQL_C_ULONG, &PartID, 0, &PartIDInd);  
  
// Retrieve and display each row of data.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   // Display the part ID and initialize the picture.  
   DisplayID(PartID, PartIDInd);  
   InitPicture();  
  
   // Retrieve the picture data in parts. Send each part and the number   
   // of bytes in each part to a function that displays it. The number   
   // of bytes is always 5000 if there were more than 5000 bytes   
   // available to return (cbBinaryBuffer > 5000). Code to check if   
   // rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
   while ((rc = SQLGetData(hstmt, 2, SQL_C_BINARY, BinaryPtr, sizeof(BinaryPtr),  
                           &BinaryLenOrInd)) != SQL_NO_DATA) {  
      NumBytes = (BinaryLenOrInd > 5000) || (BinaryLenOrInd == SQL_NO_TOTAL) ?  
                  5000 : BinaryLenOrInd;  
      DisplayNextPictPart(BinaryPtr, NumBytes);  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```  
  
 Il existe plusieurs restrictions sur l’utilisation de **SQLGetData**. En règle générale, les colonnes accessibles avec **SQLGetData**:  
  
-   Doit être accessible par ordre croissant de numéro de colonne (en raison de la façon des que colonnes d’un jeu de résultats sont lus à partir de la source de données). Par exemple, il est une erreur d’appeler **SQLGetData** pour la colonne 5 puis l’appeler pour la colonne 4.  
  
-   ne peut pas être liée.  
  
-   Doit avoir un numéro de colonne supérieur à la dernière colonne dépendante. Par exemple, si la dernière colonne dépendante est la colonne 3, il est une erreur d’appeler **SQLGetData** pour la colonne 2. Pour cette raison, les applications doivent veillez à placer les colonnes de données de type long à la fin de la liste de sélection.  
  
-   Ne peut pas être utilisé si **SQLFetch** ou **SQLFetchScroll** a été appelé pour extraire plusieurs lignes. Pour plus d’informations, consultez [à l’aide des curseurs de bloc](../../../odbc/reference/develop-app/using-block-cursors.md).  
  
 Certains pilotes n’appliquent pas ces restrictions. Applications interopérables soit partez du principe qu’ils existent ou déterminent quelles restrictions ne sont pas appliquées en appelant **SQLGetInfo** avec l’option SQL_GETDATA_EXTENSIONS.  
  
 Si l’application ne doit pas toutes les données dans un caractère ou une colonne de données binaires, elle peut réduire le trafic réseau dans les pilotes basés sur SGBD en définissant l’attribut d’instruction SQL_ATTR_MAX_LENGTH avant d’exécuter l’instruction. Cela limite le nombre d’octets de données qui seront retournées pour tout caractère ou d’une colonne binaire. Par exemple, qu'une colonne contient des documents de texte long. Une application qui parcourt la table contenant cette colonne peut avoir afficher uniquement la première page de chaque document. Bien que cet attribut d’instruction peut être simulé dans le pilote, il n’existe aucune raison pour ce faire. En particulier, si une application souhaite tronquer des données binaires ou caractères, il doit lier une petite mémoire tampon à la colonne avec **SQLBindCol** et laisser le pilote tronquer les données.
