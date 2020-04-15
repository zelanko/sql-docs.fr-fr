---
title: Fonction SQLAllocHandle (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLAllocHandle
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLAllocHandle
helpviewer_keywords:
- SQLAllocHandle function [ODBC]
ms.assetid: 6e7fe420-8cf4-4e72-8dad-212affaff317
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 178e3fad1ec062dd7f812125da66b7e21a7a4f4b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290209"
---
# <a name="sqlallochandle-function"></a>SQLAllocHandle, fonction
**Conformité**  
 Version introduite: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLAllocHandle** alloue un environnement, une connexion, une déclaration ou une poignée descripteur.  
  
> [!NOTE]  
>  Cette fonction est une fonction générique pour l’attribution des poignées qui remplace les fonctions ODBC 2.0 **SQLAllocConnect**, **SQLAllocEnv**, et **SQLAllocStmt**. Permettre aux applications appelant **SQLAllocHandle** de travailler avec ODBC 2. *x* les conducteurs, un appel à **SQLAllocHandle** est cartographié dans le gestionnaire de conducteur à **SQLAllocConnect**, **SQLAllocEnv**, ou **SQLAllocStmt**, le cas échéant. Pour plus d’informations, voir "Commentaires". Pour plus d’informations sur ce que le Driver Manager cartographie cette fonction à quand un ODBC 3. *x* application fonctionne avec un ODBC 2. *x* pilote, voir [Mapping Replacement Functions for Backward Compatibility of Applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLAllocHandle(  
      SQLSMALLINT   HandleType,  
      SQLHANDLE     InputHandle,  
      SQLHANDLE *   OutputHandlePtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *HandleType*  
 [Entrée] Le type de poignée à attribuer par **SQLAllocHandle**. Il doit s’agir de l’une des valeurs suivantes :   
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN poignée n’est utilisée que par le Gestionnaire du conducteur et le conducteur. Les applications ne doivent pas utiliser ce type de poignée. Pour plus d’informations sur SQL_HANDLE_DBC_INFO_TOKEN, voir [Developing Connection-Pool Awareness in an ODBC Driver](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 *InputHandle (en)*  
 [Entrée] Le poignée d’entrée dans le contexte de laquelle la nouvelle poignée doit être attribuée. Si *HandleType* est SQL_HANDLE_ENV, c’est SQL_NULL_HANDLE. Si *HandleType* est SQL_HANDLE_DBC, il doit s’agir d’une poignée d’environnement, et si elle est SQL_HANDLE_STMT ou SQL_HANDLE_DESC, il doit s’agir d’une poignée de connexion.  
  
 *OutputHandlePtr (en)*  
 [Sortie] Pointeur vers un tampon dans lequel retourner la poignée à la structure de données nouvellement allouée.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_INVALID_HANDLE ou SQL_ERROR.  
  
 Lors de l’attribution d’une poignée autre qu’une poignée d’environnement, si **SQLAllocHandle** retourne SQL_ERROR, il définit *OutputHandlePtr* à SQL_NULL_HDBC, SQL_NULL_HSTMT, ou SQL_NULL_HDESC, selon la valeur de *HandleType*, sauf si l’argument de sortie est un pointeur nul. L’application peut alors obtenir des informations supplémentaires à partir de la structure de données diagnostiques associées à la poignée dans l’argument *InputHandle.*  
  
## <a name="environment-handle-allocation-errors"></a>Erreurs d’allocation de gestion de l’environnement  
 L’allocation de l’environnement se produit à la fois au sein du gestionnaire de conducteur et au sein de chaque conducteur. L’erreur retournée par **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV dépend du niveau dans lequel l’erreur s’est produite.  
  
 Si le gestionnaire de conducteur ne peut pas allouer la mémoire pour * \*OutputHandlePtr* lorsque **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV est appelé, ou l’application fournit un pointeur nul pour *OutputHandlePtr*, **SQLAllocHandle** retourne SQL_ERROR. Le Gestionnaire de pilote définit*le gestionnaire de la conduite* et le SQL_NULL_HENV (à moins que l’application ne fournisse un pointeur nul, qui renvoie SQL_ERROR). Il n’y a aucune poignée avec laquelle associer des informations diagnostiques supplémentaires.  
  
 Le gestionnaire de conducteur n’appelle pas la fonction d’allocation de poignée d’environnement au niveau du conducteur jusqu’à ce que l’application appelle **SQLConnect**, **SQLBrowseConnect**, ou **SQLDriverConnect**. Si une erreur se produit dans la fonction **SQLAllocHandle** au niveau du conducteur, alors le Driver Manager-niveau **SQLConnect**, **SQLBrowseConnect**, ou LA fonction **SQLDriverConnect** retourne SQL_ERROR. La structure de données diagnostiques contient SQLSTATE IM004 (Driver’s **SQLAllocHandle** a échoué). L’erreur est retournée sur une poignée de connexion.  
  
 Pour plus d’informations sur le flux d’appels de fonction entre le gestionnaire de conducteur et un conducteur, voir [SQLConnect Fonction](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLAllocHandle** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec le *HandleType* et *poignée* appropriés réglés à la valeur *d’InputHandle*. SQL_SUCCESS_WITH_INFO (mais pas SQL_ERROR) peut être retourné pour l’argument *OutputHandle.* Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLAllocHandle** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08003|Connexion non ouverte|(DM) *L’argument de HandleType* était SQL_HANDLE_STMT ou SQL_HANDLE_DESC, mais la connexion spécifiée par l’argument *d’InputHandle* n’était pas ouverte. Le processus de connexion doit être complété avec succès (et la connexion doit être ouverte) pour que le conducteur puisse allouer une poignée de relevé ou descripteur.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le tampon*MessageText* décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|(DM) Le gestionnaire de conducteur n’a pas été en mesure d’allouer la mémoire pour la poignée spécifiée.<br /><br /> Le conducteur n’a pas été en mesure d’allouer la mémoire pour la poignée spécifiée.|  
|HY009|Utilisation invalide du pointeur nul|(DM) *L’argument de OutputHandlePtr* était un pointeur nul.|  
|HY010|Erreur de séquence de fonction|(DM) *L’argument de HandleType* était SQL_HANDLE_DBC, et **SQLSetEnvAttr** n’a pas été appelé pour définir l’attribut SQL_ODBC_VERSION environnement.<br /><br /> (DM) Une fonction d’exécution asynchrone a été appelée pour le **Main d’entrée** et était toujours en cours d’exécution lorsque la fonction **SQLAllocHandle** a été appelé avec **HandleType** mis à SQL_HANDLE_STMT ou SQL_HANDLE_DESC.|  
|HY013|Erreur de gestion de la mémoire|*L’argument de HandleType* était SQL_HANDLE_DBC, SQL_HANDLE_STMT ou SQL_HANDLE_DESC; et l’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY014|Limite sur le nombre de poignées dépassées|La limite définie par le conducteur pour le nombre de poignées pouvant être attribuées pour le type de poignée indiquée par l’argument *De HandleType* a été atteinte.|  
|HY092 HY092|Identification d’attribut/option invalide|(DM) L’argument *de HandleType* n’était pas le cas : SQL_HANDLE_ENV, SQL_HANDLE_DBC, SQL_HANDLE_STMT ou SQL_HANDLE_DESC.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|*L’argument de HandleType* était SQL_HANDLE_DESC et le conducteur était un ODBC 2. *x* conducteur.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) L’argument *de HandleType* était SQL_HANDLE_STMT, et le conducteur n’était pas un conducteur valide de l’ODBC.<br /><br /> (DM) *L’argument de HandleType* était SQL_HANDLE_DESC, et le conducteur n’est pas en faveur de l’attribution d’une poignée descripteur.|  
  
## <a name="comments"></a>Commentaires  
 **SQLAllocHandle** est utilisé pour allouer des poignées pour les environnements, les connexions, les déclarations et les descripteurs, tel que décrit dans les sections suivantes. Pour plus d’informations générales sur les poignées, voir [Poignées](../../../odbc/reference/develop-app/handles.md).  
  
 Plus d’un environnement, connexion ou poignée de relevé peut être attribué par une application à la fois si plusieurs allocations sont prises en charge par le conducteur. Dans ODBC, aucune limite n’est définie sur le nombre de poignées d’environnement, de connexion, de relevé ou descripteur qui peuvent être attribuées à tout moment. Les conducteurs peuvent imposer une limite au nombre d’un certain type de poignée qui peut être alloué à la fois; pour plus d’informations, consultez la documentation du conducteur.  
  
 Si l’application appelle **SQLAllocHandle** avec * \*OutputHandlePtr* réglé à un environnement, connexion, déclaration ou poignée descripteur qui existe déjà, le conducteur surécrit les informations associées à la *poignée,* à moins que l’application utilise la mise en commun des connexions (voir "Allocating un attribut de l’environnement pour la mise en commun de connexion" plus tard dans cette section). Le gestionnaire de pilote ne vérifie pas si la *poignée* saisie dans * \*OutputHandlePtr* est déjà utilisée, ni le contenu précédent d’une poignée avant de les écrire.  
  
> [!NOTE]  
>  Il est incorrect ODBC programmation d’application d’appeler **SQLAllocHandle** deux fois avec la même variable d’application définie pour * \*OutputHandlePtr* sans appeler **SQLFreeHandle** pour libérer la poignée avant de la réaffecter. La suréscription des poignées ODBC d’une manière qui pourrait entraîner un comportement incohérent ou des erreurs de la part des conducteurs d’ODBC.  
  
 Sur les systèmes d’exploitation qui prennent en charge plusieurs threads, les applications peuvent utiliser le même environnement, connexion, déclaration ou poignée descripteur sur différents threads. Les conducteurs doivent donc prendre en charge l’accès sécuritaire et multitâli à ces informations; une façon d’y parvenir, par exemple, est d’utiliser une section critique ou un sémaphore. Pour plus d’informations sur le threading, voir [Multithreading](../../../odbc/reference/develop-app/multithreading.md).  
  
 **SQLAllocHandle** ne fixe pas l’attribut SQL_ATTR_ODBC_VERSION environnement lorsqu’il est appelé à allouer une poignée d’environnement; l’attribut de l’environnement doit être défini par l’application, ou SQLSTATE HY010 (erreur de séquence de fonction) sera retourné lorsque **SQLAllocHandle** est appelé à allouer une poignée de connexion.  
  
 Pour les applications conformes aux normes, **SQLAllocHandle** est cartographié à **SQLAllocHandleStd** au moment de la compilation. La différence entre ces deux fonctions est que **SQLAllocHandleStd** définit l’attribut SQL_ATTR_ODBC_VERSION environnement à SQL_OV_ODBC3 quand il est appelé avec *l’argument HandleType* mis à SQL_HANDLE_ENV. Cela se fait parce que les applications conformes aux normes sont toujours ODBC 3. *x* applications. De plus, les normes n’exigent pas l’enregistrement de la version d’application. C’est la seule différence entre ces deux fonctions; sinon, ils sont identiques. **SQLAllocHandleStd** est cartographié à **SQLAllocHandle** à l’intérieur du gestionnaire du conducteur. Par conséquent, les conducteurs tiers n’ont pas à mettre en œuvre **SQLAllocHandleStd**.  
  
 Les applications ODBC 3.8 doivent être utilisées :  
  
-   **SQLAllocHandle et non SQLAllocHandleStd** pour allouer une poignée d’environnement.  
  
-   **SQLSetEnvAttr** pour définir l’attribut SQL_ATTR_ODBC_VERSION environnement à SQL_OV_ODBC3_80.  
  
## <a name="allocating-an-environment-handle"></a>Allocation d'un handle d'environnement  
 Une poignée d’environnement donne accès à des informations globales telles que des poignées de connexion valides et des poignées de connexion actives. Pour plus d’informations générales sur les poignées d’environnement, voir [Environment Handles](../../../odbc/reference/develop-app/environment-handles.md).  
  
 Pour demander une poignée d’environnement, une application appelle **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV et un *InputHandle* de SQL_NULL_HANDLE. Le conducteur alloue de la mémoire pour l’information sur l’environnement et transmet la valeur de la poignée associée dans * \*l’argument OutputHandlePtr.* L’application * \** passe la valeur OutputHandle dans tous les appels ultérieurs qui nécessitent un argument de poignée d’environnement. Pour plus d’informations, voir [Allocating the Environment Handle](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Sous la poignée d’environnement d’un gestionnaire de conducteur, s’il existe déjà une poignée d’environnement du conducteur, puis **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV n’est pas appelé dans ce conducteur quand une connexion est faite, seulement **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DBC. Si la poignée d’environnement d’un conducteur n’existe pas sous la poignée de l’environnement du gestionnaire de conducteur, SQLAllocHandle avec un HandleType de SQL_HANDLE_ENV et SQLAllocHandle avec un HandleType de SQL_HANDLE_DBC sont appelés dans le conducteur lorsque la poignée de connexion de l’environnement est connectée au conducteur.  
  
 Lorsque le gestionnaire de conducteur traite la fonction **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_ENV, il vérifie le mot clé **Trace** dans la section [ODBC] de l’information du système. S’il est réglé à 1, le Driver Manager permet de retracer l’application en cours. Si le drapeau trace est réglé, le traçage commence lorsque la poignée du premier environnement est allouée et se termine lorsque la poignée du dernier environnement est libérée. Pour plus d’informations, voir [Configuring Data Sources](../../../odbc/reference/install/configuring-data-sources.md).  
  
 Après avoir alloué une poignée d’environnement, une application doit appeler **SQLSetEnvAttr** sur la poignée environnement pour définir l’attribut SQL_ATTR_ODBC_VERSION environnement. Si cet attribut n’est pas défini avant **que SQLAllocHandle** ne soit appelé à allouer une poignée de connexion sur l’environnement, l’appel pour allouer la connexion retournera SQLSTATE HY010 (erreur de séquence de fonction). Pour plus d’informations, voir [Décerlarons la version ODBC de l’application](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md).  
  
## <a name="allocating-shared-environments-for-connection-pooling"></a>Répartition des environnements partagés pour la mise en commun des connexions  
 Les environnements peuvent être partagés entre plusieurs composants sur un seul processus. Un environnement partagé peut être utilisé par plus d’un composant en même temps. Lorsqu’un composant utilise un environnement partagé, il peut utiliser des connexions mises en commun, ce qui lui permet d’allouer et d’utiliser une connexion existante sans recréer cette connexion.  
  
 Avant d’attribuer un environnement partagé qui peut être utilisé pour la mise en commun des connexions, une application doit appeler **SQLSetEnvAttr** pour définir l’attribut SQL_ATTR_CONNECTION_POOLING environnement à SQL_CP_ONE_PER_DRIVER ou SQL_CP_ONE_PER_HENV. **SQLSetEnvAttr** dans ce cas est appelé avec *EnvironmentHandle* réglé à null, ce qui rend l’attribut un attribut de niveau de processus.  
  
 Une fois la mise en commun des connexions activée, une application appelle **SQLAllocHandle** avec l’argument *HandleType* réglé pour SQL_HANDLE_ENV. L’environnement alloué par cet appel sera un environnement implicite partagé car la mise en commun des connexions a été activée.  
  
 Lorsqu’un environnement partagé est attribué, l’environnement qui sera utilisé n’est pas déterminé jusqu’à ce que **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DBC est appelé. À ce moment-là, le gestionnaire de conducteur tente de trouver un environnement existant qui correspond aux attributs de l’environnement demandés par la demande. Si cet environnement n’existe pas, on est créé comme un environnement partagé. Le gestionnaire de chauffeur tient un compte de référence pour chaque environnement partagé; le nombre est réglé à 1 lorsque l’environnement est créé pour la première fois. Si un environnement correspondant est trouvé, la poignée de cet environnement est retournée à l’application et le nombre de références est incrémenté. Une poignée d’environnement allouée de cette manière peut être utilisée dans n’importe quelle fonction ODBC qui accepte une poignée d’environnement comme argument d’entrée.  
  
## <a name="allocating-a-connection-handle"></a>Allocation d'un handle de connexion  
 Une poignée de connexion donne accès à des informations telles que l’instruction valide et les poignées descripteur sur la connexion et si une transaction est actuellement ouverte. Pour plus d’informations générales sur les poignées de connexion, voir [Connection Handles](../../../odbc/reference/develop-app/connection-handles.md).  
  
 Pour demander une poignée de connexion, une application appelle **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DBC. *L’argument d’InputHandle* est réglé sur la poignée d’environnement qui a été retournée par l’appel à **SQLAllocHandle** qui a alloué cette poignée. Le pilote alloue la mémoire pour les informations de connexion et passe la valeur de la poignée associée de retour dans * \*OutputHandlePtr*. L’application passe la * \*valeur OutputHandlePtr* dans tous les appels ultérieurs qui nécessitent une poignée de connexion. Pour plus d’informations, voir [Allouer une poignée de connexion](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md).  
  
 Le Gestionnaire de conducteur traite la fonction **SQLAllocHandle** et appelle la fonction **SQLAllocHandle** du conducteur lorsque l’application appelle **SQLConnect**, **SQLBrowseConnect**, ou **SQLDriverConnect**. (Pour plus d’informations, voir [SQLConnect Fonction](../../../odbc/reference/syntax/sqlconnect-function.md).)  
  
 Si l’attribut SQL_ATTR_ODBC_VERSION environnement n’est pas défini avant **que SQLAllocHandle** soit appelé à allouer une poignée de connexion sur l’environnement, l’appel pour allouer la connexion retournera SQLSTATE HY010 (erreur de séquence de fonction).  
  
 Lorsqu’une application appelle **SQLAllocHandle** avec l’argument *InputHandle* réglé pour SQL_HANDLE_DBC et également réglé sur une poignée d’environnement partagée, le gestionnaire de conducteur tente de trouver un environnement partagé existant qui correspond aux attributs de l’environnement définis par l’application. S’il n’existe pas de tel environnement, on en crée un, avec un décompte de référence (maintenu par le Driver Manager) de 1. Si un environnement partagé assorti est trouvé, cette poignée est retournée à l’application et son nombre de références est incrémenté.  
  
 La connexion réelle qui sera utilisée n’est pas déterminée par le gestionnaire de conducteur jusqu’à ce que **SQLConnect** ou **SQLDriverConnect** soit appelé. Le gestionnaire de chauffeur utilise les options de connexion dans l’appel à **SQLConnect** (ou les mots clés de connexion dans l’appel à **SQLDriverConnect**) et les attributs de connexion définis après l’attribution de connexion pour déterminer quelle connexion dans le pool doit être utilisée. Pour plus d’informations, voir [SQLConnect Function](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="allocating-a-statement-handle"></a>Allocation d'un descripteur d'instruction  
 Une poignée de relevés donne accès à des renseignements sur les relevés, tels que les messages d’erreur, le nom du curseur et les renseignements sur l’état du traitement des relevés SQL. Pour obtenir des renseignements généraux sur les poignées de relevés, voir [Les poignées d’énoncés](../../../odbc/reference/develop-app/statement-handles.md).  
  
 Pour demander une poignée de relevé, une application se connecte à une source de données, puis appelle **SQLAllocHandle** avant de soumettre des relevés SQL. Dans cet appel, *HandleType* doit être réglé pour SQL_HANDLE_STMT et *InputHandle* devrait être réglé à la poignée de connexion qui a été retourné par l’appel à **SQLAllocHandle** qui a alloué cette poignée. Le conducteur alloue la mémoire pour les informations de déclaration, associe la poignée de déclaration avec la connexion spécifiée, et passe la valeur de la poignée associée de retour dans * \*OutputHandlePtr*. L’application passe la * \*valeur OutputHandlePtr* dans tous les appels ultérieurs qui nécessitent une poignée de relevé. Pour plus d’informations, voir [Allouer une poignée de déclaration](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md).  
  
 Lorsque la poignée de déclaration est attribuée, le conducteur alloue automatiquement un ensemble de quatre descripteurs et attribue les poignées de ces descripteurs aux attributs SQL_ATTR_APP_ROW_DESC, SQL_ATTR_APP_PARAM_DESC, SQL_ATTR_IMP_ROW_DESC et SQL_ATTR_IMP_PARAM_DESC. Ceux-ci sont appelés descripteurs *implicitement* attribués. Pour répartir explicitement un descripteur d’application, voir la section suivante, « Allouer une poignée descripteur ».  
  
## <a name="allocating-a-descriptor-handle"></a>Répartition d’une poignée descripteur  
 Lorsqu’une demande appelle **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_DESC, le conducteur alloue un descripteur d’application. Ceux-ci sont appelés descripteurs *explicitement* attribués. L’application ordonne à un conducteur d’utiliser un descripteur d’application explicitement attribué au lieu d’un descripteur d’application automatiquement alloué pour une poignée de relevé donné en appelant la fonction **SQLSetStmtAttr** avec l’attribut SQL_ATTR_APP_ROW_DESC ou SQL_ATTR_APP_PARAM_DESC. Un descripteur de mise en œuvre ne peut pas être attribué explicitement, pas plus qu’un descripteur de mise en œuvre ne peut être spécifié dans un appel de fonction **SQLSetStmtAttr.**  
  
 Les descripteurs explicitement attribués sont associés à une poignée de connexion au lieu d’une poignée de déclaration (comme le sont automatiquement les descripteurs alloués). Les descripteurs ne restent attribués que lorsqu’une application est effectivement connectée à la base de données. Étant donné que les descripteurs explicitement attribués sont associés à une poignée de connexion, une application peut associer un descripteur explicitement attribué à plus d’une déclaration dans une connexion. Par contre, un descripteur de demande implicitement attribué ne peut être associé à plus d’une poignée de déclaration. (Il ne peut être associé à une poignée de déclaration autre que celle pour laquelle elle a été allouée.) Les poignées descripteur explicitement attribuées peuvent être libérées explicitement soit par l’application, soit en appelant **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_DESC, soit implicitement lorsque la connexion est fermée.  
  
 Lorsque le descripteur explicitement attribué est libéré, le descripteur implicitement attribué est de nouveau associé à la déclaration. (L’attribut SQL_ATTR_APP_ROW_DESC ou SQL_ATTR_APP_PARAM_DESC pour cette déclaration est de nouveau réglé sur la poignée implicitement attribuée descripteur.) Cela est vrai pour toutes les déclarations qui ont été associées au descripteur explicitement attribué sur la connexion.  
  
 Pour plus d’informations sur les descripteurs, voir [Descriptors](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="code-example"></a>Exemple de code  
 Voir [Sample ODBC Program](../../../odbc/reference/sample-odbc-program.md), [SQLBrowseConnect Function](../../../odbc/reference/syntax/sqlbrowseconnect-function.md), [SQLConnect Function](../../../odbc/reference/syntax/sqlconnect-function.md), et [SQLSetCursorName Function](../../../odbc/reference/syntax/sqlsetcursorname-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Exécution d’une déclaration SQL|[SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Exécution d’une déclaration SQL préparée|[SQLExecute, fonction](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Libérer un environnement, une connexion, une déclaration ou une poignée descripteur|[Fonction SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Préparation d’une déclaration pour l’exécution|[Fonction SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Définir un attribut de connexion|[Fonction SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|Mise en place d’un champ descripteur|[SQLSetDescField, fonction](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|Définir un attribut d’environnement|[Fonction SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|Définir un attribut de déclaration|[Fonction SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
