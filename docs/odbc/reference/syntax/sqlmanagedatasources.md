---
title: SQLManageDataSources - France Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLManageDataSources
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLManageDataSources
helpviewer_keywords:
- SQLManageDataSources [ODBC]
ms.assetid: ac6d186f-b394-406c-94c4-c6331d1ca468
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3b572a861af3479e1543be9fda9598cc7e25d36c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290216"
---
# <a name="sqlmanagedatasources"></a>SQLManageDataSources
**Conformité**  
 Version introduite: ODBC 2.0  
  
 **Résumé**  
 **SQLManageDataSources** affiche une boîte de dialogue avec laquelle les utilisateurs peuvent configurer, ajouter et supprimer les sources de données dans les informations du système.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLManageDataSources(  
     HWND     hwnd);  
```  
  
## <a name="arguments"></a>Arguments  
 *Hwnd*  
 [Entrée] Poignée de fenêtre de parent.  
  
## <a name="returns"></a>Retours  
 **SQLManageDataSources** retourne FALSE si *hwnd n’est* pas une poignée de fenêtre valide. Sinon, elle retourne TRUE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLManageDataSources** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_REQUEST_FAILED|*Demande* a échoué|L’appel à **ConfigDSN** a échoué.|  
|ODBC_ERROR_INVALID__HWND|Poignée de fenêtre invalide|*L’argument de hwnd* était invalide ou NULL.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|L’installateur ne pouvait pas effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="managing-data-sources"></a>Gestion des sources de données  
 **SQLManageDataSources** affiche d’abord la boîte de dialogue **de l’administrateur de source de données ODBC,** comme le montre l’illustration suivante.  
  
 ![Boîte de dialogue Administrateur de sources de données ODBC](../../../odbc/reference/syntax/media/ch23e.gif "CH23E")  
  
 La boîte de dialogue affiche les sources de données répertoriées dans les informations du système sous trois onglets: **User DSN**, **System DSN**, et **File DSN**. Si l’utilisateur double-clics une source de données ou sélectionne une source de données et clique **Configurer,** **SQLManageDataSources** appelle **ConfigDSN** dans la configuration DLL avec l’option ODBC_CONFIG_DSN.  
  
 Si l’utilisateur clique **Ajouter**, **SQLManageDataSources** affiche la boîte de dialogue **Create New Data Source,** indiquée dans l’illustration suivante.  
  
 ![Boîte de dialogue Créer une nouvelle source de données](../../../odbc/reference/syntax/media/ch23f.gif "CH23F")  
  
 La boîte de dialogue affiche une liste de pilotes installés. Si l’utilisateur double-clics d’un pilote ou sélectionne un pilote et clique **sur OK,** **SQLManageDataSources** appelle **ConfigDSN** dans la configuration DLL et lui passe l’option ODBC_ADD_DSN.  
  
 Si l’utilisateur sélectionne une source de données et clique **Supprimer,** **SQLManageDataSources** demande si l’utilisateur veut supprimer la source de données. Si l’utilisateur clique **Oui,** **SQLManageDataSources** appelle **ConfigDSN** dans la configuration DLL avec l’option ODBC_REMOVE_DSN.  
  
 La boîte de dialogue **Create New Data Source** est utilisée pour ajouter ou supprimer une source de données utilisateur, une source de données système ou une source de données de fichiers.  
  
## <a name="user-dsns"></a>DNS utilisateur  
 Les DSN créés pour les utilisateurs individuels s’appelleront DSN utilisateur, afin de les distinguer des DSN système. Les DSN utilisateurs sont enregistrés comme suit dans les informations du système :  
  
 `HKEY_CURRENT_USERS`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbc.ini`  
  
## <a name="system-dsns"></a>DSN système  
 La boîte de dialogue **Create New Data Source** vous permet d’ajouter une source de données système à votre ordinateur local ou d’en supprimer une, ou de définir la configuration d’une source de données système.  
  
 Une source de données configuré avec un nom de source de données système (DSN) peut être utilisée par plus d’un utilisateur sur la même machine. Il peut également être utilisé par un service à l’échelle du système, qui peut alors accéder à la source de données, même si aucun utilisateur n’est connecté à la machine.  
  
 Un DSN système est enregistré dans l’entrée HKEY_LOCAL_MACHINE dans les informations du système plutôt que dans l’entrée HKEY_CURRENT_USER. Il n’est pas lié à un utilisateur qui se connecte avec son nom d’utilisateur particulier et mot de passe, mais peut être utilisé par n’importe quel utilisateur de cette machine ou par un service automatique à l’échelle du système. Le système DSN est, cependant, lié à une machine. Il ne prend pas en charge la capacité d’utiliser des DSN distants entre les machines. Les DSN système sont enregistrés comme suit dans les informations du système :  
  
 HKEY_LOCAL_MACHINE SOFTWARE ODBC Odbc.ini  
  
## <a name="file-dsns"></a>Fichiers DSN  
 Une source de données de fichiers n’a pas de nom de source de données, tout comme une source de données de machine, et n’est enregistrée à aucun utilisateur ou machine. Les informations de connexion pour cette source de données sont contenues dans un fichier .dsn qui peut être copié à n’importe quelle machine. Une source de données de fichiers peut être partageable, auquel cas le fichier .dsn réside sur un réseau et peut être utilisé simultanément par plusieurs utilisateurs sur le réseau tant que l’utilisateur a installé le pilote approprié. Une source de données de fichiers peut également être inshareable, auquel cas elle ne peut être utilisée que sur une seule machine.  
  
 Pour plus d’informations sur les sources de données de fichiers, voir [Connecting Using File Data Sources](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md), ou voir [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="managing-drivers"></a>Gestion des chauffeurs  
 Si l’utilisateur clique sur **l’onglet Pilotes** dans la boîte de dialogue de l’administrateur **de source de données ODBC,** **SQLManageDataSources** affiche une liste de pilotes ODBC installés sur le système, ainsi que des informations sur les pilotes. La date affichée est la date de création du conducteur, comme le montre l’illustration suivante.  
  
 ![Onglet Pilotes de la boîte de dialogue Administrateur de sources de données ODBC](../../../odbc/reference/syntax/media/ch23g.gif "ch23g ch23g")  
  
## <a name="tracing-options"></a>Options de suivi  
 Si l’utilisateur clique sur **l’onglet Tracing** dans la boîte de dialogue de l’administrateur **de source de données ODBC,** **SQLManageDataSources** affiche les options de traçage, comme le montre l’illustration suivante.  
  
 ![Onglet Traçage de la boîte de dialogue Administrateur de sources de données ODBC](../../../odbc/reference/syntax/media/ch23h.gif "Ch23h Ch23h")  
  
 Si l’utilisateur clique **Sur Démarrer Tracing Maintenant,** puis clique **sur OK,** **SQLManageDataSources** permet de tracer manuellement pour toutes les applications actuellement en cours d’exécution sur la machine.  
  
 Si l’utilisateur spécifie le nom d’un fichier de trace dans la boîte de texte **de loge Path** et clique ensuite **sur OK,** **SQLManageDataSources** définit le mot clé **TraceFile** dans la section [ODBC] des informations du système au nom spécifié.  
  
> [!IMPORTANT]  
>  La prise en charge de Visual Studio Analyzer a été supprimée à partir de Windows 8 (Visual Studio Analyzer n’a été inclus que dans les anciennes versions de Visual Studio.). Pour un autre mécanisme de dépannage, utilisez le traçage BID.  
  
 Si l’utilisateur clique **sur Start Visual Studio Analyzer** et clique ensuite sur **OK,** Visual Studio Analyzer est activé. Il reste activé jusqu’à ce que **Stop Visual Studio Analyzer** soit cliqué.  
  
 Pour plus d’informations sur la recherche, voir [Tracing](../../../odbc/reference/develop-app/tracing.md). Pour plus d’informations sur les mots clés **Trace** et **TraceFile,** voir [ODBC Subkey](../../../odbc/reference/install/odbc-subkey.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Création de sources de données|[SQLCreateDataSource (en anglais)](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|
