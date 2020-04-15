---
title: Fonction SQLGetDiagRec (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetDiagRec
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDiagRec
helpviewer_keywords:
- SQLGetDiagRec function [ODBC]
ms.assetid: ebdbac93-3d68-438f-8416-ef1f08e04269
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 39069526e254903509ddfef00b7bd4844f3d9e10
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285379"
---
# <a name="sqlgetdiagrec-function"></a>SQLGetDiagRec, fonction
**Conformité**  
 Version introduite: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLGetDiagRec** renvoie les valeurs actuelles de plusieurs domaines d’un dossier diagnostique qui contient des informations d’erreur, d’avertissement et d’état. Contrairement à **SQLGetDiagField**, qui renvoie un champ de diagnostic par appel, **SQLGetDiagRec** retourne plusieurs domaines couramment utilisés d’un dossier diagnostique, y compris le SQLSTATE, le code d’erreur natif, et le texte de message diagnostique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLGetDiagRec(  
     SQLSMALLINT     HandleType,  
     SQLHANDLE       Handle,  
     SQLSMALLINT     RecNumber,  
     SQLCHAR *       SQLState,  
     SQLINTEGER *    NativeErrorPtr,  
     SQLCHAR *       MessageText,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   TextLengthPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *HandleType*  
 [Entrée] Un identifiant de type manche qui décrit le type de poignée pour laquelle des diagnostics sont nécessaires. Doit prendre l'une des valeurs suivantes :  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN poignée n’est utilisée que par le Gestionnaire du conducteur et le conducteur. Les applications ne doivent pas utiliser ce type de poignée. Pour plus d’informations sur SQL_HANDLE_DBC_INFO_TOKEN, voir [Developing Connection-Pool Awareness in an ODBC Driver](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 *Handle*  
 [Entrée] Une poignée pour la structure de données diagnostiques, du type indiqué par *HandleType*. Si *HandleType* est SQL_HANDLE_ENV, *Handle* peut être soit une poignée d’environnement partagée ou non partagée.  
  
 *RecNumber*  
 [Entrée] Indique le dossier d’état à partir duquel la demande recherche des informations. Les dossiers d’état sont numérotés à partir de 1.  
  
 *Sqlstate*  
 [Sortie] Pointeur vers un tampon dans lequel retourner un code SQLSTATE à cinq caractères (et mettre fin à NULL) pour le dossier diagnostique *RecNumber*. Les deux premiers personnages indiquent la classe; les trois suivantes indiquent la sous-classe. Cette information est contenue dans le domaine du diagnostic SQL_DIAG_SQLSTATE. Pour plus d’informations, voir [SQLSTATEs](../../../odbc/reference/develop-app/sqlstates.md).  
  
 *NativeErrorPtr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le code d’erreur natif, spécifique à la source de données. Cette information est contenue dans le domaine du diagnostic SQL_DIAG_NATIVE.  
  
 *MessageText*  
 [Sortie] Pointeur vers un tampon dans lequel retourner la chaîne de texte de message diagnostique. Cette information est contenue dans le domaine du diagnostic SQL_DIAG_MESSAGE_TEXT. Pour le format de la chaîne, voir [Messages diagnostiques](../../../odbc/reference/develop-app/diagnostic-messages.md).  
  
 Si *MessageText* est NULL, *TextLengthPtr* retournera toujours le nombre total de caractères (à l’exclusion du caractère de terminaison nulle pour les données de caractère) disponibles pour revenir dans le tampon indiqué par *MessageText*.  
  
 *BufferLength*  
 [Entrée] Longueur du tampon*MessageText* en caractères. Il n’y a pas de durée maximale du texte du message diagnostique.  
  
 *TextLengthPtr TextLengthPtr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le nombre total de caractères (à l’exclusion du nombre de caractères requis pour le caractère de résiliation nulle) disponible pour revenir dans * \*MessageText*. Si le nombre de caractères disponibles pour revenir est supérieur à *BufferLength*, le texte de message diagnostique dans * \*MessageText* est tronqué à *BufferLength* moins la longueur d’un caractère de non-termination.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 **SQLGetDiagRec** ne poste pas de dossiers diagnostiques pour lui-même. Il utilise les valeurs de retour suivantes pour signaler le résultat de sa propre exécution :  
  
-   SQL_SUCCESS : La fonction a retourné avec succès l’information diagnostique.  
  
-   SQL_SUCCESS_WITH_INFO : Le \*tampon *MessageText* était trop petit pour contenir le message diagnostique demandé. Aucun dossier diagnostique n’a été généré. Pour déterminer qu’une troncation s’est produite, l’application doit comparer *BufferLength* au nombre réel d’octets disponibles, qui est écrit à*StringLengthPtr*.  
  
-   SQL_INVALID_HANDLE : La poignée indiquée par *HandleType* et *Handle* n’était pas une poignée valide.  
  
-   SQL_ERROR : L’un des éléments suivants s’est produit :  
  
    -   *RecNumber* était négatif ou 0.  
  
    -   *BufferLength* était moins de zéro.  
  
    -   Lors de l’utilisation de la notification asynchrone, l’opération asynchrone sur la poignée n’était pas terminée.  
  
-   SQL_NO_DATA : *RecNumber* était supérieur au nombre de dossiers diagnostiques qui existaient pour la poignée spécifiée dans *Handle.* La fonction renvoie également SQL_NO_DATA pour tout *RecNumber* positif s’il n’y a pas de dossiers diagnostiques pour *handle*.  
  
## <a name="comments"></a>Commentaires  
 Une application appelle généralement **SQLGetDiagRec** lorsqu’un appel précédent à une fonction ODBC est retourné SQL_ERROR ou SQL_SUCCESS_WITH_INFO. Cependant, parce que n’importe quelle fonction ODBC peut poster des enregistrements diagnostiques nuls ou plus chaque fois qu’il est appelé, une application peut appeler **SQLGetDiagRec** après n’importe quel appel de fonction ODBC. Une application peut appeler **SQLGetDiagRec** plusieurs fois pour retourner une partie ou la totalité des enregistrements dans la structure de données diagnostiques. ODBC n’impose aucune limite au nombre de dossiers diagnostiques qui peuvent être stockés à tout moment.  
  
 **SQLGetDiagRec** ne peut pas être utilisé pour retourner les champs de l’en-tête de la structure de données diagnostiques. *(L’argument du RecNumber* doit être supérieur à 0.) L’application doit appeler **SQLGetDiagField** à cette fin.  
  
 **SQLGetDiagRec** ne récupère que les informations diagnostiques les plus récemment associées à la poignée spécifiée dans l’argument *de poignée.* Si l’application appelle une autre fonction ODBC, à l’exception **de SQLGetDiagRec**, **SQLGetDiagField**, ou **SQLError**, toute information diagnostique des appels précédents sur la même poignée est perdue.  
  
 Une application peut numériser tous les dossiers diagnostiques en boucle, incrémentant *RecNumber*, tant que **SQLGetDiagRec** retourne SQL_SUCCESS. Les appels à **SQLGetDiagRec** ne sont pastructifs pour les champs d’en-tête et d’enregistrement. L’application peut appeler **SQLGetDiagRec** à nouveau à une date ultérieure pour récupérer un champ d’un enregistrement aussi longtemps qu’aucune autre fonction, sauf **SQLGetDiagRec**, **SQLGetDiagField**, ou **SQLError**, a été appelé dans l’intervalle. L’application peut également récupérer un nombre total de dossiers diagnostiques disponibles en appelant **SQLGetDiagField** pour récupérer la valeur du champ SQL_DIAG_NUMBER, puis en appelant **SQLGetDiagRec** que plusieurs fois.  
  
 Pour une description des champs de la structure de données diagnostiques, voir [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md). Pour plus d’informations, voir [à l’aide de SQLGetDiagRec et SQLGetDiagField](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md) et [mise en œuvre SQLGetDiagRec et SQLGetDiagField](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md).  
  
 Appeler une API autre que celle qui est exécuté asynchrone générera HY010 "Erreur de séquence de fonction". Toutefois, l’enregistrement d’erreur ne peut pas être récupéré avant la fin de l’opération asynchrone.  
  
## <a name="handletype-argument"></a>HandleType Argument  
 Chaque type de poignée peut avoir des informations diagnostiques qui lui sont associées. *L’argument de HandleType* dénote le type de poignée de l’argument *de poignée.*  
  
 Certains champs d’en-tête et d’enregistrement ne peuvent pas être retournés pour l’environnement, la connexion, l’instruction et les poignées descripteur. Les poignées pour lesquelles un champ n’est pas applicable sont indiquées dans les sections « Champs d’en-tête » et « Champs d’enregistrement » dans [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md).  
  
 Un appel à **SQLGetDiagRec** reviendra SQL_INVALID_HANDLE si *HandleType* est SQL_HANDLE_SENV, ce qui dénote une poignée d’environnement partagée. Toutefois, si *HandleType* est SQL_HANDLE_ENV, *Handle* peut être soit une poignée d’environnement partagée ou non partagée.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Obtenir un champ d’un dossier diagnostique ou un champ de l’en-tête diagnostique|[Fonction SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Exemple de programme ODBC](../../../odbc/reference/sample-odbc-program.md)
