---
title: Fonction SQLSetEnvAttr (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetEnvAttr
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLSetEnvAttr
helpviewer_keywords:
- SQLSetEnvAttr function [ODBC]
ms.assetid: 0343241c-4b15-4d4b-aa2b-2e8ab5215cd2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 640b1e6947d67b92e2b7f8e623597e1d99d4a877
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299539"
---
# <a name="sqlsetenvattr-function"></a>Fonction SQLSetEnvAttr
**Conformité**  
 Version introduite: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLSetEnvAttr** définit les attributs qui régissent les aspects des environnements.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLSetEnvAttr(  
     SQLHENV      EnvironmentHandle,  
     SQLINTEGER   Attribute,  
     SQLPOINTER   ValuePtr,  
     SQLINTEGER   StringLength);  
```  
  
## <a name="arguments"></a>Arguments  
 *EnvironnementHandle*  
 [Entrée] Poignée de l’environnement.  
  
 *Attribut*  
 [Entrée] Attribuer à l’ensemble, énuméré dans "Commentaires".  
  
 *ValuePtr*  
 [Entrée] Pointeur à la valeur à associer à *Attribut*. Selon la valeur de *l’attribut*, *ValuePtr* sera une valeur d’intégrateur 32 bits ou pointer vers une chaîne de caractères non terminée.  
  
 *StringLength (en)*  
 [Entrée] Si *ValuePtr* pointe vers une chaîne de caractères ou un tampon binaire, cet argument doit être la longueur de *'ValuePtr*. Pour les données de chaîne de caractère, cet argument doit contenir le nombre d’octets dans la chaîne.  
  
 Si *ValuePtr* est un intégrateur, *StringLength* est ignoré.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLSetEnvAttr** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_ENV et une *poignée* *d’EnvironnementHandle*. Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLSetEnvAttr** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire. Si un pilote ne prend pas en charge un attribut d’environnement, l’erreur ne peut être retournée que pendant le temps de connexion.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01S02|Valeur de l’option modifiée|Le conducteur n’a pas supporté la valeur spécifiée dans *ValuePtr* et a remplacé une valeur similaire. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY009|Utilisation invalide du pointeur nul|L’argument d’attribut a identifié un attribut d’environnement qui exigeait une valeur de chaîne, et l’argument *de ValuePtr* était un pointeur nul.|  
|HY010|Erreur de séquence de fonction|(DM) Une poignée de connexion a été allouée sur *EnvironmentHandle*.<br /><br /> (DM) **SQL_ATTR_ODBC_VERSION** n’a pas été fixé avec **SQLSetEnvAttr** et *Attribut* n’est pas égal à **SQL_ATTR_ODBC_VERSION**. Vous n’avez pas besoin de définir **SQL_ATTR_ODBC_VERSION** explicitement si vous utilisez **SQLAllocHandleStd**.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY024|Valeur d’attribut invalide|Compte tenu de la valeur *d’attribut* spécifiée, une valeur invalide a été spécifiée dans *ValuePtr*.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|*L’argument de StringLength* était inférieur à 0, mais n’était pas SQL_NTS.|  
|HY092 HY092|Identification d’attribut/option invalide|(DM) La valeur spécifiée pour l’argument *Attribut* n’était pas valide pour la version d’ODBC prise en charge par le conducteur.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|La valeur spécifiée pour l’argument *Attribut* était un attribut d’environnement ODBC valide pour la version d’ODBC pris en charge par le conducteur, mais n’a pas été pris en charge par le conducteur.<br /><br /> (DM) *L’argument d’attribut* était SQL_ATTR_OUTPUT_NTS, et *ValuePtr* était SQL_FALSE.|  
  
## <a name="comments"></a>Commentaires  
 Une application ne peut appeler **SQLSetEnvAttr** que si aucune poignée de connexion n’est allouée à l’environnement. Tous les attributs de l’environnement définis avec succès par l’application pour l’environnement persistent jusqu’à ce que **SQLFreeHandle** soit appelé sur l’environnement. Plus d’une poignée d’environnement peut être attribuée simultanément dans ODBC *3.x*.  
  
 Le format d’information défini par *ValuePtr* dépend de *l’attribut*spécifié . **SQLSetEnvAttr** acceptera l’information d’attribut dans l’un des deux formats différents : une chaîne de caractères non terminée ou une valeur integer 32 bits. Le format de chacun est noté dans la description de l’attribut.  
  
 Il n’y a pas d’attributs d’environnement spécifiques au conducteur.  
  
 Les attributs de connexion ne peuvent pas être définis par un appel à **SQLSetEnvAttr**. Essayer de le faire retournera SQLSTATE HY092 (Attribut invalide / identifiant d’option).  
  
|*Attribut*|*Contenu ValuePtr*|  
|-----------------|-------------------------|  
|SQL_ATTR_CONNECTION_POOLING (ODBC 3.8)|Une valeur SQLUINTEGER 32 bits qui permet ou désactive la mise en commun des connexions au niveau de l’environnement. Les valeurs suivantes sont utilisées :<br /><br /> SQL_CP_OFF la mise en commun de connexion est désactivée. Il s’agit de la valeur par défaut.<br /><br /> SQL_CP_ONE_PER_DRIVER une seule piscine de connexion est prise en charge pour chaque conducteur. Chaque connexion dans une piscine est associée à un seul conducteur.<br /><br /> SQL_CP_ONE_PER_HENV un pool de connexion unique est pris en charge pour chaque environnement. Chaque connexion dans une piscine est associée à un seul environnement.<br /><br /> SQL_CP_DRIVER_AWARE - Utilisez la fonction de sensibilisation au pool de connexion du conducteur, si elle est disponible. Si le conducteur ne prend pas en charge la connaissance de la piscine de connexion, SQL_CP_DRIVER_AWARE est ignorée et SQL_CP_ONE_PER_HENV est utilisée. Pour plus d’informations, voir [Driver-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md). Dans un environnement où certains conducteurs prennent en charge et où certains conducteurs ne prennent pas en charge la sensibilisation au pool de connexion, SQL_CP_DRIVER_AWARE peuvent permettre la fonction de sensibilisation au pool de connexion sur les conducteurs qui soutiennent les conducteurs, mais il est équivalent à mettre en place pour SQL_CP_ONE_PER_HENV sur les conducteurs qui ne prennent pas en charge la fonction de sensibilisation au pool de connexion.<br /><br /> La mise en commun des connexions est activée en appelant **SQLSetEnvAttr** pour définir l’attribut SQL_ATTR_CONNECTION_POOLING à SQL_CP_ONE_PER_DRIVER ou SQL_CP_ONE_PER_HENV. Cet appel doit être effectué avant que l’application n’attribue l’environnement partagé pour lequel la mise en commun des connexions doit être activée. La poignée d’environnement dans l’appel à **SQLSetEnvAttr** est réglée à null, ce qui rend SQL_ATTR_CONNECTION_POOLING un attribut de niveau processus. Une fois la mise en commun des connexions activée, l’application alloue ensuite un environnement implicite partagé en appelant **SQLAllocHandle** avec l’argument *InputHandle* réglé pour SQL_HANDLE_ENV.<br /><br /> Une fois que la mise en commun des connexions a été activée et qu’un environnement partagé a été sélectionné pour une application, SQL_ATTR_CONNECTION_POOLING ne peut pas être réinitialisé pour cet environnement, car **SQLSetEnvAttr** est appelé avec une poignée d’environnement nul lors de la configuration de cet attribut. Si cet attribut est défini alors que la mise en commun des connexions est déjà activée sur un environnement partagé, l’attribut n’affecte que les environnements partagés qui sont attribués par la suite.<br /><br /> Il est également possible d’activer la mise en commun des connexions sur un environnement. Notez ce qui suit au sujet de la mise en commun des connexions en environnement :<br /><br /> - Permettre la mise en commun des connexions sur une poignée NULL est un attribut de niveau processus. Les environnements attribués par la suite seront un environnement partagé et hériteront du paramètre de mise en commun des connexions au niveau du processus.<br />- Une fois qu’un environnement est attribué, une application peut encore modifier son paramètre de piscine de connexion.<br />- Si la mise en commun des connexions environment est activée et que le conducteur de la connexion utilise la mise en commun du conducteur, la mise en commun de l’environnement est préférable.<br /><br /> SQL_ATTR_CONNECTION_POOLING est mis en œuvre à l’intérieur du Driver Manager. Un conducteur n’a pas besoin de mettre en œuvre SQL_ATTR_CONNECTION_POOLING. Les applications ODBC 2.0 et 3.0 peuvent définir cet attribut d’environnement.<br /><br /> Pour plus d’informations, consultez [ODBC Connection Pooling](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md).|  
|SQL_ATTR_CP_MATCH (ODBC 3.0)|Une valeur SQLUINTEGER 32 bits qui détermine comment une connexion est choisie à partir d’un pool de connexion. Lorsque **SQLConnect** ou **SQLDriverConnect** est appelé, le gestionnaire de conducteur détermine quelle connexion est réutilisée à partir de la piscine. Le Gestionnaire de pilote essaie de faire correspondre les options de connexion dans l’appel et les attributs de connexion définis par l’application aux mots clés et aux attributs de connexion des connexions dans le pool. La valeur de cet attribut détermine le niveau de précision des critères correspondants.<br /><br /> Les valeurs suivantes sont utilisées pour définir la valeur de cet attribut :<br /><br /> SQL_CP_STRICT_MATCH - Seules les connexions qui correspondent exactement aux options de connexion dans l’appel et les attributs de connexion définis par l’application sont réutilisées. Il s’agit de la valeur par défaut.<br /><br /> SQL_CP_RELAXED_MATCH - Connexions avec des mots clés de chaîne de connexion correspondants peuvent être utilisés. Les mots clés doivent correspondre, mais tous les attributs de connexion ne doivent pas correspondre.<br /><br /> Pour plus d’informations sur la façon dont le Driver Manager effectue le match en vous connectant à une connexion mise en commun, voir [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md). Pour plus d’informations sur la mise en commun des connexions, voir [ODBC Connection Pooling](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md).|  
|SQL_ATTR_ODBC_VERSION (ODBC 3.0)|Un intégrant 32 bits qui détermine si certaines fonctionnalités présentent un comportement ODBC *2.x* ou un comportement ODBC *3.x.* Les valeurs suivantes sont utilisées pour définir la valeur de cet attribut :<br /><br /> SQL_OV_ODBC3_80 - Le driver Manager et le conducteur présentent le comportement suivant ODBC 3.8:<br /><br /> - Le conducteur revient et s’attend à des codes ODBC *3.x* pour la date, l’heure et l’humidité du temps.<br />- Le conducteur retourne ODBC *3.x* SQLSTATE codes lorsque **SQLError**, **SQLGetDiagField**, ou **SQLGetDiagRec** est appelé.<br />- *L’argument CatalogName* dans un appel à **SQLTables** accepte un modèle de recherche.<br />- Le Driver Manager prend en charge l’extéabilité du type de données C. Pour plus d’informations sur l’extéabilité de type de données C, voir [C Data Types in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).<br /><br /> Pour plus d’informations, voir [What’s New in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).<br /><br /> SQL_OV_ODBC3 - Le driver Manager et le conducteur présentent le comportement suivant ODBC *3.x:*<br /><br /> - Le conducteur revient et s’attend à des codes ODBC *3.x* pour la date, l’heure et l’humidité du temps.<br />- Le conducteur retourne ODBC *3.x* SQLSTATE codes lorsque **SQLError**, **SQLGetDiagField**, ou **SQLGetDiagRec** est appelé.<br />- *L’argument CatalogName* dans un appel à **SQLTables** accepte un modèle de recherche.<br />- Le Gestionnaire de pilote ne prend pas en charge l’extéabilité du type de données C.<br /><br /> SQL_OV_ODBC2 - Le Driver Manager et le conducteur présentent le comportement suivant ODBC *2.x.* Ceci est particulièrement utile pour une application ODBC *2.x* travaillant avec un pilote ODBC *3.x.*<br /><br /> - Le conducteur revient et s’attend à des codes ODBC *2.x* pour la date, l’heure et l’humidité du temps.<br />- Le conducteur retourne ODBC *2.x* SQLSTATE codes lorsque **SQLError**, **SQLGetDiagField**, ou **SQLGetDiagRec** est appelé.<br />- *L’argument CatalogName* dans un appel à **SQLTables** n’accepte pas un modèle de recherche.<br />- Le Gestionnaire de pilote ne prend pas en charge l’extéabilité du type de données C.<br /><br /> Une application doit définir cet attribut d’environnement avant d’appeler toute fonction qui a un argument SQLHENV, ou l’appel retournera SQLSTATE HY010 (erreur de séquence de fonction). Il est spécifique au conducteur si un comportement supplémentaire existe pour ces indicateurs environnementaux.<br /><br /> - Pour plus [d’informations, voir Décerlarons la version ODBC de l’application](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) et [les changements de comportement](../../../odbc/reference/develop-app/behavioral-changes.md).|  
|SQL_ATTR_OUTPUT_NTS (ODBC 3.0)|Un intégrant 32 bits qui détermine comment le conducteur retourne les données de chaîne. Si SQL_TRUE, le conducteur renvoie les données de la chaîne non terminées. Si SQL_FALSE, le conducteur ne retourne pas les données de chaîne non terminées.<br /><br /> Cet attribut est par défaut à SQL_TRUE. Un appel à **SQLSetEnvAttr** pour le mettre à SQL_TRUE retourne SQL_SUCCESS. Un appel à **SQLSetEnvAttr** pour le régler pour SQL_FALSE renvois SQL_ERROR et SQLSTATE HYC00 (fonction facultative non mise en œuvre).|  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Répartition d’une poignée|[SQLAllocHandle, fonction](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Retourner le réglage d’un attribut de l’environnement|[SQLGetEnvAttr, fonction](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Nouveautés d’ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
