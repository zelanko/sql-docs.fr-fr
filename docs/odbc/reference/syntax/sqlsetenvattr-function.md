---
title: SQLSetEnvAttr, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetEnvAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetEnvAttr
helpviewer_keywords:
- SQLSetEnvAttr function [ODBC]
ms.assetid: 0343241c-4b15-4d4b-aa2b-2e8ab5215cd2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 61b83ee255e580c557bfae9923d67735c63c3912
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62982204"
---
# <a name="sqlsetenvattr-function"></a>Fonction SQLSetEnvAttr
**Conformité**  
 Version introduite : Conformité aux normes 3.0 de ODBC : ISO 92  
  
 **Résumé**  
 **SQLSetEnvAttr** définit les attributs qui régissent les aspects des environnements.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SQLRETURN SQLSetEnvAttr(  
     SQLHENV      EnvironmentHandle,  
     SQLINTEGER   Attribute,  
     SQLPOINTER   ValuePtr,  
     SQLINTEGER   StringLength);  
```  
  
## <a name="arguments"></a>Arguments  
 *EnvironmentHandle*  
 [Entrée] Handle d’environnement.  
  
 *Attribute*  
 [Entrée] Attribut à définir, répertoriés dans « Commentaires ».  
  
 *ValuePtr*  
 [Entrée] Pointeur vers la valeur à associer à *attribut*. Selon la valeur de *attribut*, *ValuePtr* sera une valeur d’entier 32 bits ou pointer vers une chaîne de caractères se terminant par null.  
  
 *StringLength*  
 [Entrée] Si *ValuePtr* pointe vers une chaîne de caractères ou une mémoire tampon binaire, cet argument doit être la longueur de **ValuePtr*. Pour les données de chaîne de caractères, cet argument doit contenir le nombre d’octets dans la chaîne.  
  
 Si *ValuePtr* est un entier, *StringLength* est ignoré.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLSetEnvAttr** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_ HANDLE_ENV et un *gérer* de *EnvironmentHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLSetEnvAttr** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire. Si un pilote ne prend pas en charge un attribut de l’environnement, l’erreur peut être retourné uniquement pendant les temps de connexion.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01S02|Valeur d’option modifiée|Le pilote ne prenait pas en charge la valeur spécifiée dans *ValuePtr* et remplacé une valeur similaire. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY009|Utilisation non valide de pointeur null|L’argument d’attribut identifié un attribut d’environnement qui requiert une valeur de chaîne, et le *ValuePtr* argument était un pointeur null.|  
|HY010|Erreur de séquence de fonction|(DM) un handle de connexion a été alloué sur *EnvironmentHandle*.<br /><br /> (DM) **SQL_ATTR_ODBC_VERSION** n’a pas été défini avec **SQLSetEnvAttr** et *attribut* n’est pas égal à **SQL_ATTR_ODBC_VERSION**. Vous n’avez pas besoin de définir **SQL_ATTR_ODBC_VERSION** explicitement si vous utilisez **SQLAllocHandleStd**.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY024|Valeur d’attribut non valide|Étant donné le spécifié *attribut* , une valeur non valide a été spécifiée dans *ValuePtr*.|  
|HY090|Longueur de chaîne ou une mémoire tampon non valide|Le *StringLength* argument était inférieure à 0 mais n’était pas SQL_NTS.|  
|HY092|Identificateur d’option/attribut non valide|(DM) la valeur spécifiée pour l’argument *attribut* n’était pas valide pour la version d’ODBC pris en charge par le pilote.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité optionnelle non implémentée|La valeur spécifiée pour l’argument *attribut* a un attribut d’environnement ODBC valide pour la version d’ODBC pris en charge par le pilote, mais n’était pas pris en charge par le pilote.<br /><br /> (DM) le *attribut* SQL_ATTR_OUTPUT_NTS, a été l’argument et *ValuePtr* a été SQL_FALSE.|  
  
## <a name="comments"></a>Commentaires  
 Une application peut appeler **SQLSetEnvAttr** uniquement si aucun handle de connexion n’est alloué sur l’environnement. Tous les attributs d’environnement a été définies par l’application pour l’environnement persistent jusqu'à **SQLFreeHandle** est appelée sur l’environnement. Plus d’un handle d’environnement peut être alloué simultanément dans ODBC 3 *.x*.  
  
 Le format des informations définies via *ValuePtr* dépend spécifié *attribut*. **SQLSetEnvAttr** acceptera les informations d’attribut dans un des deux formats : une chaîne de caractères se terminant par null ou une valeur d’entier 32 bits. Le format de chacun d’eux est indiqué dans la description de l’attribut.  
  
 Il n’existe aucun attribut d’environnement spécifique au pilote.  
  
 Attributs de connexion ne peut pas être définis par un appel à **SQLSetEnvAttr**. Cette tentative retourne SQLSTATE HY092 (identificateur d’option/attribut non valide).  
  
|*Attribute*|*ValuePtr* contenu|  
|-----------------|-------------------------|  
|SQL_ATTR_CONNECTION_POOLING (ODBC 3.8)|Une valeur SQLUINTEGER 32 bits qui active ou désactive le regroupement de connexions au niveau de l’environnement. Les valeurs suivantes sont utilisées :<br /><br /> SQL_CP_OFF = connexion le regroupement est mis hors tension. Il s'agit du paramètre par défaut.<br /><br /> SQL_CP_ONE_PER_DRIVER = un seul pool de connexions est pris en charge pour chaque pilote. Chaque connexion dans un pool est associée à un seul pilote.<br /><br /> SQL_CP_ONE_PER_HENV = un seul pool de connexions est pris en charge pour chaque environnement. Chaque connexion dans un pool est associée à un environnement.<br /><br /> SQL_CP_DRIVER_AWARE = utiliser la fonctionnalité de reconnaissance de pool de connexions du pilote, si elle est disponible. Si le pilote ne prend pas en charge la reconnaissance des pools de connexion, SQL_CP_DRIVER_AWARE est ignorée et SQL_CP_ONE_PER_HENV est utilisé. Pour plus d’informations, consultez [Driver-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md). Dans un environnement où certains pilotes prennent en charge et certains pilotes ne prennent pas en charge la reconnaissance des pools de connexion, SQL_CP_DRIVER_AWARE peuvent activer la fonctionnalité de reconnaissance de pool de connexions sur celles prenant en charge des pilotes, mais il revient à affecter à SQL_CP_ONE_PER_HENV sur les pilotes qui ne prennent pas en charge la fonctionnalité de reconnaissance de pool de connexions.<br /><br /> Le regroupement de connexions est activé en appelant **SQLSetEnvAttr** à la valeur de l’attribut SQL_ATTR_CONNECTION_POOLING SQL_CP_ONE_PER_DRIVER ou SQL_CP_ONE_PER_HENV. Cet appel doit être effectué avant l’application alloue l’environnement partagé, pour quelle connexion de regroupement doit être activée. Le handle d’environnement dans l’appel à **SQLSetEnvAttr** est définie sur null, ce qui rend SQL_ATTR_CONNECTION_POOLING un attribut au niveau du processus. Une fois que le regroupement de connexions est activé, puis l’application alloue un environnement partagé implicit en appelant **SQLAllocHandle** avec la *InputHandle* argument défini à SQL_HANDLE_ENV.<br /><br /> Une fois que le regroupement de connexions a été activé et un environnement partagé a été sélectionné pour une application, SQL_ATTR_CONNECTION_POOLING ne peut pas être réinitialisé pour cet environnement, car **SQLSetEnvAttr** est appelée avec un environnement null handle lors de la définition de cet attribut. Si cet attribut est défini alors que le regroupement de connexions est déjà activé sur un environnement partagé, l’attribut affecte uniquement les environnements partagés qui sont allouées par la suite.<br /><br /> Il est également possible d’activer le regroupement de connexions dans un environnement. Notez les points suivants concernant le regroupement de connexions environnement :<br /><br /> -Activation d’un handle NULL de regroupement de connexions est un attribut au niveau du processus. Environnements alloués par la suite seront un environnement partagé et hériteront la paramètre de regroupement de connexions de niveau processus.<br />-Une fois un environnement est alloué, une application peut toujours modifier son paramètre de pool de connexion.<br />-Si le regroupement de connexions environnement est activé et les pilotes de la connexion utilise le regroupement de pilote, le regroupement d’environnement prend de préférence.<br /><br /> SQL_ATTR_CONNECTION_POOLING est implémentée dans le Gestionnaire de pilotes. Un pilote n’a pas besoin d’implémenter SQL_ATTR_CONNECTION_POOLING. ODBC 2.0 et 3.0 applications peuvent définir cet attribut de l’environnement.<br /><br /> Pour plus d’informations, consultez [ODBC Connection Pooling](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md).|  
|SQL_ATTR_CP_MATCH (ODBC 3.0)|Une valeur SQLUINTEGER 32 bits qui détermine la façon dont une connexion est choisie à partir d’un pool de connexions. Lorsque **SQLConnect** ou **SQLDriverConnect** est appelée, le Gestionnaire de pilotes détermine quelle connexion est réutilisée à partir du pool. Le Gestionnaire de pilotes essaie les options de connexion dans l’appel et les attributs de connexion définies par l’application pour les mots clés et les attributs de connexion des connexions dans le pool. La valeur de cet attribut détermine le niveau de précision des critères de correspondance.<br /><br /> Les valeurs suivantes sont utilisées pour définir la valeur de cet attribut :<br /><br /> SQL_CP_STRICT_MATCH = uniquement les connexions qui correspondent exactement aux options de connexion dans l’appel et la connexion définies par l’application des attributs sont réutilisées. Il s'agit du paramètre par défaut.<br /><br /> SQL_CP_RELAXED_MATCH = connexions avec correspondance de chaîne de connexion mots clés peuvent être utilisés. Mots clés doivent correspondre, mais pas tous les attributs de connexion doivent correspondre.<br /><br /> Pour plus d’informations sur la façon dont le Gestionnaire de pilotes effectue la correspondance dans la connexion à une connexion regroupée, consultez [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md). Pour plus d’informations sur le regroupement de connexions, consultez [le regroupement de connexions ODBC](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md).|  
|SQL_ATTR_ODBC_VERSION (ODBC 3.0)|Un entier 32 bits qui détermine si certaines fonctionnalités présente ODBC 2 *.x* comportement ou ODBC 3 *.x* comportement. Les valeurs suivantes sont utilisées pour définir la valeur de cet attribut :<br /><br /> SQL_OV_ODBC3_80 = le Gestionnaire de pilote et comportement du pilote pièce à ODBC 3.8 le suivant :<br /><br /> -Le pilote retourne et nécessite que ODBC 3. *x* codes pour la date, time et timestamp.<br />-Le pilote retourne ODBC 3. *x* SQLSTATE codes lorsque **SQLError**, **SQLGetDiagField**, ou **SQLGetDiagRec** est appelée.<br />-Le *CatalogName* argument dans un appel à **SQLTables** accepte un modèle de recherche.<br />-Le Gestionnaire de pilotes prend en charge l’extensibilité du type de données C. Pour plus d’informations sur l’extensibilité de type de données C, consultez [des Types de données C dans ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).<br /><br /> Pour plus d’informations, consultez [What ' s New in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).<br /><br /> SQL_OV_ODBC3 = le Gestionnaire de pilote et pièce pilote le 3 ODBC suivantes *.x* comportement :<br /><br /> -Le pilote retourne et attend que ODBC 3 *.x* codes pour la date, time et timestamp.<br />-Le pilote retourne ODBC 3 *.x* SQLSTATE codes lorsque **SQLError**, **SQLGetDiagField**, ou **SQLGetDiagRec** est appelée.<br />-Le *CatalogName* argument dans un appel à **SQLTables** accepte un modèle de recherche.<br />-Le Gestionnaire de pilotes ne prend pas en charge l’extensibilité du type de données C.<br /><br /> SQL_OV_ODBC2 = le Gestionnaire de pilote et de la pièce de pilote ODBC 2 suivantes *.x* comportement. Cela est particulièrement utile pour un ODBC 2 *.x* application fonctionne avec un ODBC 3 *.x* pilote.<br /><br /> -Le pilote retourne et attend d’ODBC 2 *.x* codes pour la date, time et timestamp.<br />-Le pilote retourne ODBC 2 *.x* SQLSTATE codes lorsque **SQLError**, **SQLGetDiagField**, ou **SQLGetDiagRec** est appelée.<br />-Le *CatalogName* argument dans un appel à **SQLTables** n’accepte pas d’un modèle de recherche.<br />-Le Gestionnaire de pilotes ne prend pas en charge l’extensibilité du type de données C.<br /><br /> Une application doit définir cet attribut d’environnement avant d’appeler n’importe quelle fonction qui a un argument SQLHENV ou l’appel retourne SQLSTATE HY010 (erreur de séquence de fonction). Il est spécifique au pilote, si un comportement supplémentaire existe pour ces indicateurs de l’environnement.<br /><br /> -Pour plus d’informations, consultez [déclarant ODBC Version l’Application](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) et [des changements de comportement](../../../odbc/reference/develop-app/behavioral-changes.md).|  
|SQL_ATTR_OUTPUT_NTS (ODBC 3.0)|Entier 32 bits qui détermine comment le pilote retourne les données de type chaîne. Si SQL_TRUE, le pilote retourne les données de chaîne se terminant par null. Si SQL_FALSE, le pilote ne retourne pas de données de type chaîne se terminant par null.<br /><br /> Cet attribut par défaut est SQL_TRUE. Un appel à **SQLSetEnvAttr** à lui SQL_TRUE retourne SQL_SUCCESS. Un appel à **SQLSetEnvAttr** à lui retourne SQL_FALSE SQL_ERROR et SQLSTATE HYC00 (fonctionnalité facultative non implémentée).|  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Allocation d’un handle|[SQLAllocHandle, fonction](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Retourner le paramètre d’un attribut d’environnement|[SQLGetEnvAttr, fonction](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Nouveautés d’ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
