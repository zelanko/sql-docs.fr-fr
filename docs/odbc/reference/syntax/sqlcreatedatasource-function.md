---
title: SQLCreateDataSource, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba02c28f3243b623695e3e087490ef3f73c60385
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53204338"
---
# <a name="sqlcreatedatasource-function"></a>SQLCreateDataSource, fonction
**Conformité**  
 Version introduite : ODBC VERSION 2.0  
  
 **Résumé**  
 **SQLCreateDataSource** affiche une boîte de dialogue avec laquelle l’utilisateur peut ajouter une source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL SQLCreateDataSource(  
     HWND    hwnd,  
     LPSTR   lpszDS);  
```  
  
## <a name="arguments"></a>Arguments  
 *HWND*  
 [Entrée] Handle de fenêtre parente.  
  
 *lpszDS*  
 [Entrée] Nom de source de données. *lpszDS* peut être un pointeur null ou une chaîne vide.  
  
## <a name="returns"></a>Valeur renvoyée  
 **SQLCreateDataSource** retourne la valeur TRUE si la source de données est créée. Sinon, elle retourne FALSE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLCreateDataSource** retourne FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur du programme d’installation générale|Une erreur s’est produite pour lequel aucune erreur d’installation spécifique s’est produite.|  
|ODBC_ERROR_INVALID_HWND|Handle de fenêtre non valide|Le *hwnd* argument était non valide ou NULL.|  
|ODBC_ERROR_INVALID_DSN|Source de données non valide|Le *lpszDS* argument contenue une chaîne qui n’était pas valide pour une source de données.|  
|ODBC_ERROR_REQUEST_FAILED|*Demande* a échoué|L’appel à **ConfigDSN** avec l’option ODBC_ADD_DSN a échoué.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Impossible de charger la bibliothèque le programme d’installation de pilote ou de convertisseur|La bibliothèque d’installation de pilote n’a pas pu être chargée.|  
|ODBC_ERROR_USER_CANCELED|Opération de l’utilisateur a annulé|L’utilisateur a annulé la création d’une source de données.|  
|ODBC_ERROR_CREATE_DSN_FAILED|La source de données demandée n’a pas pu être créer|Ne peut pas se connecter à la base de données ; l’appel à **SQLDriverConnect** pour une source de données de fichier n’a pas retourné d’une connexion réussie.<br /><br /> N’a pas pu écrire dans le fichier.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|Le programme d’installation n’a pas pu effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 Si *hwnd* a la valeur null, **SQLCreateDataSource** retourne FALSE. Sinon, elle affiche le **créer une nouvelle Source de données** boîte de dialogue avec une page d’Assistant pour choisir le type de source de données à configurer, comme indiqué dans l’illustration suivante.  
  
 ![Créer la boîte de dialogue Nouvelle Source de données : sélectionner le type](../../../odbc/reference/syntax/media/ch23a.gif "CH23A")  
  
 L’option par défaut est **Source de données de fichier**. Lorsqu’une source de données a été choisie et **suivant** activé, la page d’Assistant suivante qui contient une liste de pilotes installés s’affiche.  
  
 ![Créer la boîte de dialogue Nouvelle Source de données : sélection du pilote](../../../odbc/reference/syntax/media/ch23b.gif "CH23B")  
  
 Si **Annuler** est activé, la boîte de dialogue disparaît de la zone et **SQLCreateDataSource** retourne FALSE avec le code d’erreur de ODBC_ERROR_USER_CANCELED. Si le **Source de données utilisateur** ou **Source de données système** option a été sélectionnée, le **avancé** bouton n’est pas disponible.  
  
 Lorsque le **suivant** bouton est activé, une des actions suivantes se produit, selon le type de données source a été sélectionnée :  
  
-   Si **Source de données de fichier** a été sélectionnée, une page d’Assistant s’affiche pour l’utilisateur à entrer un nom de fichier.  
  
-   Si **Source de données utilisateur** ou **Source de données système** a été sélectionnée, une page d’Assistant affichant le type de source de données et le pilote s’affiche pour la révision et à quel moment **Terminer** est Cliquez sur la source de données est configurée.  
  
 Si **avancé** vous cliquez sur à partir de la page de l’Assistant créer une nouvelle Source de données, une page d’Assistant s’affiche pour l’utilisateur à entrer des informations spécifiques au pilote. Dans la zone de texte de cette boîte de dialogue, tapez le pilote et les mots clés séparés par des retours, comme indiqué dans l’illustration suivante.  
  
 ![Boîte de dialogue Paramètres de création de fichier DSN avance](../../../odbc/reference/syntax/media/ch23c.gif "CH23C")  
  
 Vous trouverez des mots clés spécifiques au pilote supplémentaires sous la description de **SQLDriverConnect**. Tout sauf **DSN** sont autorisés.  
  
 La valeur par défaut pour le **vérifier cette connexion** option a la valeur TRUE. Cette valeur par défaut s’applique cette page d’Assistant est activée ou non. Si **OK** est activé, la chaîne spécifiée dans la zone de texte et la **vérifier cette connexion** valeur d’option sont mis en cache. (Si le **fermer** bouton ou **Annuler** est activé, un qui vient d’être entré les informations spécifiques au pilote sont perdues, car la chaîne spécifiée dans la zone de texte et le **vérifier cette connexion** valeur de l’option ne sont pas mises en cache.)  
  
 Si **Source de données de fichier** a été sélectionné dans la première page de l’Assistant, puis après un pilote a été sélectionné et les valeurs de mot clé ont été entrées dans la page de l’Assistant avancé, l’utilisateur est invité à entrer un nom de fichier. Cliquez sur **Parcourir** pour rechercher un nom de fichier, auquel cas le répertoire par défaut dans le **Parcourir** boîte est spécifiée par une combinaison du chemin d’accès spécifié par CommonFileDir dans HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\Windows\CurrentVersion et « ODBC\DataSources ». (Si CommonFileDir était « C:\Program Files\Common Files », le répertoire par défaut serait à « C:\Program Files\Common Files\ODBC\Data Sources ».)  
  
 Quand un nom de fichier a été entré et **suivant** est activé, le fichier le nom entré est activé pour la validité par rapport aux règles d’affectation de noms de fichier standards du système d’exploitation. Si le nom de fichier n’est pas valide, une boîte de message d’erreur informe l’utilisateur qu’un nom de fichier non valide a été entré. Une fois que l’utilisateur accuse réception de la boîte de message, le focus est renvoyé à la page d’Assistant dans lequel le nom de fichier est entré. Si le nom de fichier est valide, une page d’Assistant qui montre les paires mot clé-valeur sélectionnée s’affiche pour la révision, comme indiqué dans l’illustration suivante.  
  
 ![Créer la boîte de dialogue Nouvelle Source de données : passez en revue](../../../odbc/reference/syntax/media/ch23d.gif "CH23D")  
  
 Si **Terminer** est cliqué et **Source de données de fichier** a été sélectionné comme type de source de données et si le **vérifier cette connexion** option est TRUE,  **SQLDriverConnect** est appelée avec le **SAVEFILE** et **pilote** mots clés. Le *DriverCompletion* argument est défini sur SQL_DRIVER_COMPLETE. Le nom de fichier pour le **SAVEFILE** mot clé est le nom qui a été entré ou sélectionné et le nom du pilote pour le **pilote** mot clé est le nom qui a été choisi. Si une chaîne de connexion spécifiques au pilote a été spécifiée dans la page de l’Assistant avancé, cette chaîne est ajoutée après le **pilote** mot clé.  
  
 Si **SQLDriverConnect** retourne SQL_SUCCESS, le Gestionnaire de pilotes a créé le fichier DSN. **SQLCreateDataSource** retourne la valeur TRUE. Si **SQLDriverConnect** ne retourne SQL_SUCCESS, un message d’avertissement zone indique qu’une connexion ne peut pas être établie à la source de données. Une source de données avec les informations de connexion minimale peut encore être créé. Cette boîte de message permet à l’utilisateur soit annuler ou poursuivre la création de fichier DSN.  
  
 Si l’utilisateur choisit de poursuivre la création de la source de données, ce processus se poursuit comme si le **vérifier cette connexion** option ont été définies sur FALSE. Si l’utilisateur choisit d’annuler, la valeur FALSE est retournée pour **SQLCreateDataSource** avec un code d’erreur de ODBC_ERROR_CREATE_DSN_FAILED.  
  
 Si **Source de données de fichier** a été sélectionné comme type de source de données et la **vérifier cette connexion** option a la valeur FALSE, une source de données de fichier est créé avec le **pilote** mot clé et spécifié par l’utilisateur chaîne de connexion (le cas échéant) à partir de la page de l’Assistant avancé. Si la création du fichier a réussi, la valeur TRUE est renvoyée pour **SQLCreateDataSource**. Si la création du fichier n’a pas réussie, une boîte de message d’erreur informe l’utilisateur avec l’erreur qui a été retourné à partir du système d’exploitation. Valeur FALSE est retournée pour **SQLCreateDataSource** avec un code d’erreur de ODBC_ERROR_CREATE_DSN_FAILED. Pour plus d’informations sur les fichiers sources de données, consultez [se connectant à l’aide de fichiers Sources de données](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md), ou consultez [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Si **utilisateur** ou **Source de données système** a été sélectionné comme type de source de données, **ConfigDSN** dans le programme d’installation du pilote bibliothèque est appelée avec le ODBC_ADD_DSN  *fréquents*. Pour plus d’informations, consultez [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Gestion des sources de données|[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|
