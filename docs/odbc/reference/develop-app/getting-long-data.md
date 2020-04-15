---
title: Obtenir des données longues (en anglais) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: da901c22eb26af063397b4af184179ebe5c75924
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298989"
---
# <a name="getting-long-data"></a>Obtention de données de type Long
Les DBMS définissent les *données longues* comme n’importe quel personnage ou données binaires sur une certaine taille, telles que 255 caractères. Ces données peuvent être assez petites pour être stockées dans un seul tampon, comme une description en partie de plusieurs milliers de caractères. Cependant, il pourrait être trop long à stocker dans la mémoire, tels que les documents texte longs ou bitmaps. Étant donné que ces données ne peuvent pas être stockées dans un seul tampon, elles sont récupérées auprès du conducteur dans des pièces avec **SQLGetData** après que les autres données de la rangée ont été récupérées.  
  
> [!NOTE]  
>  Une application peut effectivement récupérer n’importe quel type de données avec **SQLGetData**, pas seulement de longues données, bien que seuls les données de caractère et binaires peuvent être récupérées en pièces. Toutefois, si les données sont assez petites pour tenir dans un seul tampon, il n’y a généralement aucune raison d’utiliser **SQLGetData**. Il est beaucoup plus facile de lier un tampon à la colonne et de laisser le pilote retourner les données dans le tampon.  
  
 Pour récupérer de longues données d’une colonne, une application appelle d’abord **SQLFetchScroll** ou **SQLFetch** pour passer à une rangée et récupérer les données pour les colonnes liées. L’application appelle ensuite **SQLGetData**. **SQLGetData** a les mêmes arguments que **SQLBindCol**: une poignée de déclaration; un numéro de colonne; le type de données C, l’adresse et la durée des fourre-tout d’une variable d’application; et l’adresse d’un tampon longueur/indicateur. Les deux fonctions ont les mêmes arguments parce qu’elles exécutent essentiellement la même tâche : elles décrivent à la fois une variable d’application pour le conducteur et spécifient que les données d’une colonne particulière doivent être retournées dans cette variable. Les principales différences sont que **SQLGetData** est appelé après une rangée est récupérée (et est parfois appelé *liaison tardive* pour cette raison) et que la liaison spécifiée par **SQLGetData** ne dure que pour la durée de l’appel.  
  
 En ce qui concerne une seule colonne, **SQLGetData** se comporte comme **SQLFetch**: Il récupère les données pour la colonne, les convertit au type de variable d’application, et les retourne dans cette variable. Il retourne également la longueur d’entrée des données dans le tampon longueur/indicateur. Pour plus d’informations sur la façon dont **SQLFetch** retourne les données, voir [Fetching a Row of Data](../../../odbc/reference/develop-app/fetching-a-row-of-data.md).  
  
 **SQLGetData** diffère de **SQLFetch** à un égard important. S’il est appelé plus d’une fois de suite pour la même colonne, chaque appel renvoie une partie successive des données. Chaque appel, à l’exception du dernier appel, renvoie SQL_SUCCESS_WITH_INFO et SQLSTATE 01004 (données de chaîne, droite tronquées); le dernier appel SQL_SUCCESS. C’est ainsi que **SQLGetData** est utilisé pour récupérer de longues données dans les pièces. Lorsqu’il n’y a plus de données à retourner, **SQLGetData** retourne SQL_NO_DATA. L’application est responsable de mettre les données longues ensemble, ce qui pourrait signifier concatenating les parties des données. Chaque partie est annulée; l’application doit supprimer le caractère de résiliation nulle si elle concatenant les pièces. La récupération des données dans les pièces peut être effectuée pour les signets à longueur variable ainsi que pour d’autres données longues. La valeur retournée dans la durée/indicateur tampon diminue dans chaque appel par le nombre d’octets retournés dans l’appel précédent, bien qu’il soit courant pour le conducteur d’être incapable de découvrir la quantité de données disponibles et de retourner une longueur d’octet de SQL_NO_TOTAL. Par exemple :  
  
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
  
 Il existe plusieurs restrictions sur l’utilisation **de SQLGetData**. En général, les colonnes accessibles avec **SQLGetData**:  
  
-   Il faut accéder de l’ordre de l’augmentation du nombre de colonnes (en raison de la façon dont les colonnes d’un ensemble de résultats sont lues à partir de la source de données). Par exemple, c’est une erreur d’appeler **SQLGetData** pour la colonne 5, puis l’appeler pour la colonne 4.  
  
-   On ne peut pas lier.  
  
-   Doit avoir un nombre de colonnes plus élevé que la dernière colonne liée. Par exemple, si la dernière colonne liée est la colonne 3, c’est une erreur d’appeler **SQLGetData** pour la colonne 2. Pour cette raison, les applications doivent s’assurer de placer de longues colonnes de données à la fin de la liste de sélection.  
  
-   On ne peut pas utiliser si **SQLFetch** ou **SQLFetchScroll** ont été appelés pour récupérer plus d’une rangée. Pour plus d’informations, voir [Utilisation des curseurs de bloc](../../../odbc/reference/develop-app/using-block-cursors.md).  
  
 Certains conducteurs n’appliquent pas ces restrictions. Les demandes interopérables devraient soit présumer qu’elles existent, soit déterminer quelles restrictions ne sont pas appliquées en appelant **SQLGetInfo** avec l’option SQL_GETDATA_EXTENSIONS.  
  
 Si l’application n’a pas besoin de toutes les données d’une colonne de caractère ou de données binaires, elle peut réduire le trafic réseau dans les pilotes basés sur DBMS en définissant l’attribut de l’SQL_ATTR_MAX_LENGTH déclaration avant d’exécuter la déclaration. Cela limite le nombre d’octets de données qui seront retournés pour n’importe quel personnage ou colonne binaire. Supposons, par exemple, qu’une colonne contient de longs documents texte. Une application qui parcourt la table contenant cette colonne peut avoir à afficher seulement la première page de chaque document. Bien que cet attribut d’instruction puisse être simulé dans le conducteur, il n’y a aucune raison de le faire. En particulier, si une application veut tronquer des données de caractère ou binaires, elle doit lier un petit tampon à la colonne avec **SQLBindCol** et laisser le conducteur tronquer les données.
