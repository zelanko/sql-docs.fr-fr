---
title: Fonction ConfigDSN ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- ConfigDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigDSN
helpviewer_keywords:
- ConfigDSN [ODBC]
ms.assetid: 01ced74e-c575-4a25-83f5-bd7d918123f8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fbae126c819088bd277621b207454503a86c8955
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306040"
---
# <a name="configdsn-function"></a>ConfigDSN, fonction
**Conformité**  
 Version introduite: ODBC 1.0  
  
 **Résumé**  
 **ConfigDSN** ajoute, modifie ou supprime les sources de données des informations du système. Il peut inciter l’utilisateur à obtenir des informations de connexion. Il peut être dans le pilote DLL ou une configuration séparée DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL ConfigDSN(  
     HWND     hwndParent,  
     WORD     fRequest,  
     LPCSTR   lpszDriver,  
     LPCSTR   lpszAttributes);  
```  
  
## <a name="arguments"></a>Arguments  
 *hwndParent*  
 [Entrée] Poignée de fenêtre de parent. La fonction n’affichera pas de boîtes de dialogue si la poignée est nulle.  
  
 *fRequest*  
 [Entrée] Type de demande. *L’argument de fRequest* doit contenir l’une des valeurs suivantes :  
  
 ODBC_ADD_DSN : Ajoutez une nouvelle source de données.  
  
 ODBC_CONFIG_DSN : Configurer (modifier) une source de données existante.  
  
 ODBC_REMOVE_DSN : Supprimez une source de données existante.  
  
 *lpszDriver (en)*  
 [Entrée] Description du pilote (généralement le nom du DBMS associé) présentée aux utilisateurs au lieu du nom du conducteur physique.  
  
 *lpszAttributes*  
 [Entrée] Une liste doublement nulle des attributs sous forme de paires de mots clés. Pour plus d’informations, voir "Commentaires".  
  
## <a name="returns"></a>Retours  
 La fonction retourne VRAI si elle est réussie, FALSE si elle échoue.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **ConfigDSN** retourne FALSE, une valeur * \*pfErrorCode* associée est affichée sur le tampon d’erreur de l’installateur par un appel à **SQLPostInstallerError** et peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Poignée de fenêtre invalide|*L’argument de hwndParent* était invalide.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Paires de mots clés invalides|*L’argument lpszAttributes* contenait une erreur de syntaxe.|  
|ODBC_ERROR_INVALID_NAME|Nom de conducteur ou traducteur invalide|*L’argument de lpszDriver* était invalide. Il n’a pas été trouvé dans le registre.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Type invalide de demande|*L’argument de fRequest* n’était pas l’un des suivants :<br /><br /> ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN|  
|ODBC_ERROR_REQUEST_FAILED|*Demande* a échoué|Impossible d’effectuer l’opération demandée par l’argument *de fRequest.*|  
|ODBC_ERROR_DRIVER_SPECIFIC|Erreur spécifique au conducteur ou au traducteur|Une erreur spécifique au conducteur pour laquelle il n’y a pas d’erreur d’installateur ODBC définie. *L’argument de SzError* dans un appel à la fonction **SQLPostInstallerError** devrait contenir le message d’erreur spécifique au conducteur.|  
  
## <a name="comments"></a>Commentaires  
 **ConfigDSN** reçoit des informations de connexion de l’installateur DLL comme une liste d’attributs sous la forme de paires de mots clés. Chaque paire est terminée avec un byte nul, et la liste entière est terminée avec un byte nul. (C’est-à-dire que deux octets nuls marquent la fin de la liste.) Les espaces ne sont pas autorisés autour du signe égal dans la paire de valeur de mot-clé. **ConfigDSN** peut accepter des mots clés qui ne sont pas des mots clés valides pour **SQLBrowseConnect** et **SQLDriverConnect**. **ConfigDSN** ne prend pas nécessairement en charge tous les mots clés valides pour **SQLBrowseConnect** et **SQLDriverConnect**. (**ConfigDSN** n’accepte pas le mot clé **DRIVER.)** Les mots clés utilisés par la fonction **ConfigDSN** doivent prendre en charge toutes les options nécessaires pour recréer la source de données à l’aide de la fonction de configuration AUTO de l’installateur. Lorsque les utilisations des valeurs **ConfigDSN** et les valeurs de chaîne de connexion sont les mêmes, les mêmes mots clés doivent être utilisés.  
  
 Comme dans **SQLBrowseConnect** et **SQLDriverConnect**, les mots clés et leurs valeurs ne devraient pas contenir le **[]{}(),;? Les \*** caractères et la valeur du mot clé **DSN** ne peuvent pas se composer uniquement de blancs. En raison de la grammaire du registre, les mots\\clés et les noms de source de données ne peuvent pas contenir le caractère de barre oblique inverse.  
  
 **ConfigDSN** devrait appeler **SQLValidDSN** pour vérifier la durée du nom de la source de données et vérifier qu’aucun personnage invalide n’est inclus dans le nom. Si le nom de source de données est plus long que SQL_MAX_DSN_LENGTH ou inclut des caractères non valides, **SQLValidDSN** renvoie une erreur et **ConfigDSN** renvoie une erreur. La longueur du nom de la source de données est également vérifiée par **SQLWriteDSNToIni**.  
  
 Par exemple, pour configurer une source de données qui nécessite un identifiant d’utilisateur, un mot de passe et un nom de base de données, une application de configuration peut passer les paires de mots clés suivantes :  
  
```  
DSN=Personnel Data\0UID=Smith\0PWD=Sesame\0DATABASE=Personnel\0\0  
```  
  
 Pour plus d’informations sur ces mots clés, consultez [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) et la documentation de chaque conducteur.  
  
 Pour afficher une boîte de dialogue, *hwndParent* ne doit pas être nul.  
  
## <a name="adding-a-data-source"></a>Ajout d'une source de données  
 Si un nom de source de données est transmis à **ConfigDSN** dans *lpszAttributes*, **ConfigDSN** vérifie que le nom est valide. Si le nom de source de données correspond à un nom de source de données existant et *que le nom hwndParent* est nul, **ConfigDSN** surmene le nom existant. S’il correspond à un nom existant et *hwndParent n’est* pas nul, **ConfigDSN** invite l’utilisateur à sous-rôdre le nom existant.  
  
 Si *lpszAttributes* contient suffisamment d’informations pour se connecter à une source de données, **ConfigDSN** peut ajouter la source de données ou afficher une boîte de dialogue avec laquelle l’utilisateur peut modifier les informations de connexion. Si *lpszAttributes* ne contient pas suffisamment d’informations pour se connecter à une source de données, **ConfigDSN** doit déterminer les informations nécessaires; si *hwndParent n’est* pas nul, il affiche une boîte de dialogue pour récupérer les informations de l’utilisateur.  
  
 Si **ConfigDSN** affiche une boîte de dialogue, il doit afficher toutes les informations de connexion qui lui sont transmises dans *lpszAttributes*. En particulier, si un nom de source de données lui a été transmis, **ConfigDSN** affiche ce nom, mais ne permet pas à l’utilisateur de le modifier. **ConfigDSN** peut fournir des valeurs par défaut pour les informations de connexion qui ne lui sont pas transmises dans *lpszAttributes*.  
  
 Si **ConfigDSN** ne peut pas obtenir des informations de connexion complètes pour une source de données, il renvoie FALSE.  
  
 Si **ConfigDSN** peut obtenir des informations de connexion complètes pour une source de données, il appelle **SQLWriteDSNToIni** dans l’installateur DLL pour ajouter la nouvelle spécification source de données au fichier Odbc.ini (ou registre). **SQLWriteDSNToIni** ajoute le nom de source de données à la section [ODBC Data Sources], crée la section de spécifications de source de données et ajoute le mot clé **DRIVER** avec la description du conducteur comme valeur. **ConfigDSN** appelle **SQLWritePrivateProfileString** dans l’installateur DLL pour ajouter les mots clés et les valeurs supplémentaires utilisés par le conducteur.  
  
## <a name="modifying-a-data-source"></a>Modification d’une source de données  
 Pour modifier une source de données, un nom de source de données doit être transmis à **ConfigDSN** dans *lpszAttributes*. **ConfigDSN** vérifie que le nom de la source de données se trouve dans le fichier Odbc.ini (ou registre).  
  
 Si *hwndParent* est nul, **ConfigDSN** utilise les informations contenues dans *lpszAttributes* pour modifier les informations contenues dans le fichier Odbc.ini (ou registre). Si *hwndParent n’est* pas nul, **ConfigDSN** affiche une boîte de dialogue en utilisant les informations dans *lpszAttributes*; pour les informations non dans *lpszAttributes*, il utilise des informations provenant des informations du système. L’utilisateur peut modifier les informations avant **que ConfigDSN** ne les stocke dans les informations du système.  
  
 Si le nom de source de données a été modifié, **ConfigDSN** appelle **d’abord SQLRemoveDSNFromIni** dans l’installateur DLL pour supprimer la spécification source de données existante du fichier Odbc.ini (ou registre). Il suit ensuite les étapes de la section précédente pour ajouter les nouvelles spécifications de source de données. Si le nom de source de données n’a pas été modifié, **ConfigDSN** appelle **SQLWritePrivateProfileString** dans l’installateur DLL pour apporter d’autres modifications. **ConfigDSN** ne peut pas supprimer ou modifier la valeur du mot clé **pilote.**  
  
## <a name="deleting-a-data-source"></a>Suppression d’une source de données  
 Pour supprimer une source de données, un nom de source de données doit être transmis à **ConfigDSN** dans *lpszAttributes*. **ConfigDSN** vérifie que le nom de la source de données se trouve dans le fichier Odbc.ini (ou registre). Il appelle ensuite **SQLRemoveDSNFromIni** dans l’installateur DLL pour supprimer la source de données.  
  
## <a name="note"></a>Remarque
 Si vous écrivez une version Unicode de cette routine, il doit être appelé **ConfigDSNW**, avec des arguments LPCWSTR au lieu de LPCSTR.
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Ajout, modification ou suppression d’une source de données|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Obtenir une valeur du fichier Odbc.ini ou du registre|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|  
|Suppression de la source de données par défaut|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Suppression d’un nom de source de données de Odbc.ini (ou registre)|[SQLRemoveDSNDeIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|Ajout d’un nom de source de données à Odbc.ini (ou registre)|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|  
|Rédaction d’une valeur pour le fichier Odbc.ini ou le registre|[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
