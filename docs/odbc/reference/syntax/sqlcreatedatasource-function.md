---
title: Fonction SQLCreateDataSource (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCreateDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLCreateDataSource
helpviewer_keywords:
- SQLCreateDataSource function [ODBC]
ms.assetid: 76ee851a-dca9-40cc-8e9e-eb3f74e560ee
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 94dc0d6d6f3b5bc96ae41aecda5b46f119cff85c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301199"
---
# <a name="sqlcreatedatasource-function"></a>SQLCreateDataSource, fonction
**Conformité**  
 Version introduite: ODBC 2.0  
  
 **Résumé**  
 **SQLCreateDataSource** affiche une boîte de dialogue avec laquelle l’utilisateur peut ajouter une source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLCreateDataSource(  
     HWND    hwnd,  
     LPSTR   lpszDS);  
```  
  
## <a name="arguments"></a>Arguments  
 *Hwnd*  
 [Entrée] Poignée de fenêtre de parent.  
  
 *lpszDS (lpszDS)*  
 [Entrée] Nom de source de données. *lpszDS* peut être un pointeur nul ou une chaîne vide.  
  
## <a name="returns"></a>Retours  
 **SQLCreateDataSource** renvoie TRUE si la source de données est créée. Sinon, il retourne FALSE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLCreateDataSource** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_INVALID_HWND|Poignée de fenêtre invalide|*L’argument de hwnd* était invalide ou NULL.|  
|ODBC_ERROR_INVALID_DSN|DSN invalide|*L’argument de lpszDS* contenait une chaîne qui était invalide pour un DSN.|  
|ODBC_ERROR_REQUEST_FAILED|*Demande* a échoué|L’appel à **ConfigDSN** avec l’option ODBC_ADD_DSN a échoué.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Impossible de charger le conducteur ou la bibliothèque d’installation de traducteur|La bibliothèque d’installation du conducteur n’a pas pu être chargée.|  
|ODBC_ERROR_USER_CANCELED|Opération annulée par l’utilisateur|L’utilisateur a annulé la création d’une nouvelle source de données.|  
|ODBC_ERROR_CREATE_DSN_FAILED|Impossible de créer le DSN demandé|Impossible de se connecter à la base de données; l’appel à **SQLDriverConnect** pour un fichier DSN n’a pas retourné une connexion réussie.<br /><br /> Impossible d’écrire au fichier.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|L’installateur ne pouvait pas effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 Si *hwnd* est nul, **SQLCreateDataSource** retourne FALSE. Dans le cas contraire, il affiche la boîte de dialogue **Create New Data Source** avec une page d’assistant pour choisir le type de source de données à configurer, comme indiqué dans l’illustration suivante.  
  
 ![Boîte de dialogue Créer une nouvelle source de données : sélection du type](../../../odbc/reference/syntax/media/ch23a.gif "CH23A")  
  
 L’option par défaut est **Source de données de fichiers**. Lorsqu’une source de données a été choisie et **que Next** a cliqué, la page assistante suivante qui contient une liste de pilotes installés s’affiche.  
  
 ![Boîte de dialogue Créer une nouvelle source de données : sélection du pilote](../../../odbc/reference/syntax/media/ch23b.gif "CH23B")  
  
 Si **Cancel** est cliqué, la boîte de dialogue disparaît et **SQLCreateDataSource** renvoie FALSE avec le code d’erreur de ODBC_ERROR_USER_CANCELED. Si **l’option Source de données utilisateur** ou source de données **système** a été sélectionnée, le bouton **Advanced** n’est pas disponible.  
  
 Lorsque le bouton **Suivant** est cliqué, l’un des éléments suivants se produira, selon le type de source de données sélectionnée :  
  
-   Si **la source de données de fichier** a été sélectionnée, une page d’assistant est affichée pour que l’utilisateur saisissait un nom de fichier.  
  
-   Si **la source de données utilisateur** ou la source de données **système** a été sélectionnée, une page d’assistant affichant le type de source de données et le pilote est affichée pour examen, et lorsque **la finition** est cliqué, la source de données est configurée.  
  
 Si **Advanced** est cliqué à partir de la page de l’assistant Create New Data Source, une page d’assistant est affichée pour que l’utilisateur saisis des informations spécifiques au conducteur. Dans la boîte de texte de cette boîte de dialogue, tapez le conducteur et les mots clés séparés par les retours, comme le montre l’illustration suivante.  
  
 ![Boîte de dialogue Paramètres avancés de création de sources de données fichier](../../../odbc/reference/syntax/media/ch23c.gif "CH23C")  
  
 D’autres mots clés spécifiques au conducteur peuvent être trouvés sous la description de **SQLDriverConnect**. Tous sauf **DSN** sont autorisés.  
  
 La valeur par défaut de l’option **Vérifier cette connexion** est VRAI. Ce défaut s’applique si cette page d’assistant est activée ou non. Si **OK** est cliqué, la chaîne spécifiée dans la boîte de texte et la valeur **de l’option Vérifier cette connexion** sont mises en cache. (Si le bouton **Close** ou **Cancel** est cliqué, toute information nouvellement saisie spécifique au conducteur est perdue parce que la chaîne spécifiée dans la boîte de texte et la valeur **de l’option Vérifier cette connexion** ne sont pas mises en cache.)  
  
 Si **La source de données de fichier** a été sélectionnée dans la première page d’assistant, puis après qu’un pilote a été sélectionné et que les valeurs de mots clés ont été saisies dans la page assistante avancée, l’utilisateur est invité à entrer un nom de fichier. Cliquez **sur Parcourir** pour rechercher un nom de fichier, auquel cas l’annuaire par défaut dans la boîte De **navigation** est spécifié par une combinaison du chemin spécifié par CommonFileDir dans HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-Windows-CurrentVersion et "ODBC-DataSources". (Si CommonFileDir était « Fichiers communs de programme de C , l’annuaire par défaut serait « C : Fichiers de programme - Fichiers communs -ODBC-Sources de données »).)  
  
 Lorsqu’un nom de fichier a été entré et **que Next** est cliqué, le nom du fichier inscrit est vérifié pour la validité par rapport aux règles standard de nommage du système d’exploitation. Si le nom du fichier n’est pas valide, une boîte de message d’erreur informe l’utilisateur qu’un nom de fichier invalide a été entré. Une fois que l’utilisateur reconnaît la boîte de message, l’accent est retourné à la page de l’assistant dans lequel le nom du fichier est entré. Si le nom du fichier est valide, une page d’assistant qui affiche les paires de mots clés sélectionnées est affichée pour examen, comme indiqué dans l’illustration suivante.  
  
 ![Boîte de dialogue Créer une nouvelle source de données : vérification](../../../odbc/reference/syntax/media/ch23d.gif "CH23D")  
  
 Si **La finition** est cliqué et que La source de données de **fichier** a été sélectionnée comme type de source de données, et si **l’option Vérifier cette connexion** est VRAI, **SQLDriverConnect** est appelé avec les mots clés **SAVEFILE** et **DRIVER.** *L’argument de DriverCompletion* est prêt à SQL_DRIVER_COMPLETE. Le nom de fichier pour le mot clé **SAVEFILE** est le nom qui a été entré ou choisi, et le nom du pilote pour le mot clé **DRIVER** est le nom qui a été choisi. Si une chaîne de connexion spécifique au conducteur a été spécifiée dans la page Assistant Advanced, cette chaîne est jointe après le mot clé **DRIVER.**  
  
 Si **SQLDriverConnect** revient SQL_SUCCESS, le gestionnaire de pilote a créé le Fichier DSN. **SQLCreateDataSource** revient VRAI. Si **SQLDriverConnect** ne retourne pas SQL_SUCCESS, une boîte de message d’avertissement indique qu’une connexion n’a pas pu être faite à la source de données. Un DSN avec un minimum d’informations de connexion peut encore être créé. Cette boîte de message permet à l’utilisateur d’annuler ou de continuer avec la création de Fichier DSN.  
  
 Si l’utilisateur choisit de continuer à créer le DSN, ce processus se poursuit comme si l’option **Vérifier cette connexion** était définie à FALSE. Si l’utilisateur choisit d’annuler, FALSE est retourné pour **SQLCreateDataSource** avec un code d’erreur de ODBC_ERROR_CREATE_DSN_FAILED.  
  
 Si **La source de données de fichier** a été sélectionnée comme type source de données et que **l’option Vérifier cette connexion** est FALSE, un DSN de fichier est créé avec le mot clé **DRIVER** et la chaîne de connexion spécifiée par l’utilisateur (le cas échéant) à partir de la page assistante avancée. Si la création du fichier a été couronnée de succès, TRUE est retourné pour **SQLCreateDataSource**. Si la création de fichiers n’a pas été couronnée de succès, une boîte de message d’erreur informe l’utilisateur avec n’importe quelle erreur a été retournée du système d’exploitation. FALSE est retourné pour **SQLCreateDataSource** avec un code d’erreur de ODBC_ERROR_CREATE_DSN_FAILED. Pour plus d’informations sur les sources de données de fichiers, voir [Connecting Using File Data Sources](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md), ou voir [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Si **l’utilisateur** ou **la source de données système** a été sélectionné comme type de source de données, **ConfigDSN** dans la bibliothèque d’installation du conducteur est appelé avec le ODBC_ADD_DSN *fRequest*. Pour plus d’informations, voir [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Gérer les sources de données|[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|
