---
title: Sqlinstalldriverex, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallDriverEx
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallDriverEx
helpviewer_keywords:
- SQLInstallDriverEx function [ODBC]
ms.assetid: 1dd74544-f4e9-46e1-9b5f-c11d84fdab4c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4b6bae692efdb1d89642eea52e499b0fb2800377
ms.sourcegitcommit: fc6a6eedcea2d98c93e33d39c1cecd99fbc9a155
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49169322"
---
# <a name="sqlinstalldriverex-function"></a>SQLInstallDriverEx, fonction
**Conformité**  
 Version introduite : ODBC 3.0  
  
 **Résumé**  
 **SQLInstallDriverEx** ajoute des informations sur le pilote à l’entrée de fichier Odbcinst.ini dans les informations système et incrémente le pilote *UsageCount* par 1. Toutefois, si une version du pilote existe déjà mais le *UsageCount* valeur pour le pilote n’existe pas, la nouvelle *UsageCount* a la valeur 2.  
  
 Cette fonction ne copie pas réellement de tous les fichiers. Il est responsable de programme appelant pour copier les fichiers du pilote dans le répertoire cible correctement.  
  
 La fonctionnalité de **SQLInstallDriverEx** est également accessible avec [ODBCCONF. EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL SQLInstallDriverEx(  
     LPCSTR    lpszDriver,  
     LPCSTR    lpszPathIn,  
     LPSTR     lpszPathOut,  
     WORD      cbPathOutMax,  
     WORD *    pcbPathOut,  
     WORD      fRequest,  
     LPDWORD   lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszDriver*  
 [Entrée] Description du pilote (généralement le nom du SGBD associé) présentée aux utilisateurs au lieu du nom de pilote physique. Le *lpszDriver* argument doit contenir une liste doublement se terminant par null de paires mot clé-valeur décrivant le pilote. Pour plus d’informations sur les paires mot clé-valeur, consultez [sous-clés de spécification de pilote](../../../odbc/reference/install/driver-specification-subkeys.md). Pour plus d’informations sur la chaîne doublement se terminant par null, consultez [ConfigDSN, fonction](../../../odbc/reference/syntax/configdsn-function.md).  
  
 *lpszPathIn*  
 [Entrée] Chemin d’accès complet du répertoire cible de l’installation, ou un pointeur null. Si *lpszPathIn* est un pointeur null, les pilotes seront installés dans le répertoire système.  
  
 *lpszPathOut*  
 [Sortie] Chemin d’accès du répertoire cible où le pilote doit être installé. Si le pilote n’a pas encore été installé, *lpszPathOut* doit être le même que *lpszPathIn*. Si le pilote a été précédemment installé, *lpszPathOut* est le chemin d’accès de l’installation précédente.  
  
 *cbPathOutMax*  
 [Entrée] Longueur de *lpszPathOut*.  
  
 *pcbPathOut*  
 [Sortie] Nombre total d’octets (sans le caractère de fin de la valeur null) disponibles à renvoyer dans *lpszPathOut*. Si le nombre d’octets à retourner est supérieur ou égal à *cbPathOutMax*, le chemin de sortie dans *lpszPathOut* est tronqué à *cbPathOutMax* moins le caractère du caractère nul de terminaison. Le *pcbPathOut* argument peut être un pointeur null.  
  
 *fréquents*  
 [Entrée] Type de requête. Le *fréquents* argument doit contenir l’une des valeurs suivantes :  
  
 ODBC_INSTALL_INQUIRY : Savoir où un pilote peut être installé.  
  
 ODBC_INSTALL_COMPLETE : Terminer la requête de l’installation.  
  
 *lpdwUsageCount*  
 [Sortie] Le décompte d’utilisation du pilote après que cette fonction a été appelée.  
  
 Applications ne doivent pas définir le décompte d’utilisation. ODBC gère ce nombre.  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne la valeur TRUE si elle réussit, FALSE en cas d’échec.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLInstallDriverEx** retourne FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur du programme d’installation générale|Une erreur s’est produite pour lequel aucune erreur d’installation spécifique s’est produite.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Longueur de la mémoire tampon non valide|Le *lpszPathOut* argument n’était pas assez grand pour contenir le chemin de sortie. La mémoire tampon contient le chemin d’accès tronquée.<br /><br /> Le *cbPathOutMax* argument était égale à 0, et *fréquents* a été ODBC_INSTALL_COMPLETE.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Type de demande non valide|Le *fréquents* argument n’est pas une des opérations suivantes :<br /><br /> ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Paires mot clé-valeur non valide|Le *lpszDriver* argument contenait une erreur de syntaxe.|  
|ODBC_ERROR_INVALID_PATH|Chemin d’installation non valide|Le *lpszPathIn* argument contenait un chemin d’accès non valide.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Impossible de charger la bibliothèque le programme d’installation de pilote ou de convertisseur|La bibliothèque d’installation de pilote n’a pas pu être chargée.|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Séquence de paramètres non valide|Le *lpszDriver* argument ne contenait pas d’une liste de paires mot clé-valeur.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Impossible d’incrémenter ou décrémenter le décompte d’utilisation de composant|Le programme d’installation a échoué incrémenter le décompte d’utilisation du pilote.|  
  
## <a name="comments"></a>Commentaires  
 Le *lpszDriver* argument est une liste d’attributs sous la forme de paires mot clé-valeur. Chaque paire se termine par un octet null, et la liste entière se termine avec un octet null. (Autrement dit, deux octets null marquent la fin de la liste.) Le format de cette liste est la suivante :  
  
 _pilote-desc_ **\\**0Driver**=**_pilote-DLL-filename_ **\\**0 [le programme d’installation**=**_le programme d’installation-DLL-filename_<b>\\</b>0]  
  
 [_pilote-attr-mot-Clé1_**=**_value1_<b>\\</b>0] [_pilote-attr-MotClé2_  **=** _value2_<b>\\</b>0]... <b> \\ </b>0  
  
 où \0 est un octet null et *pilote-attr-keywordn* est n’importe quel attribut de pilote mot clé. Les mots clés doivent apparaître dans l’ordre spécifié. Par exemple, supposons qu’un pilote pour les fichiers de texte mis en forme possède de pilote séparé et le programme d’installation DLL et pouvez utiliser des fichiers avec les extensions .txt et .csv. Le *lpszDriver* argument pour ce pilote peut être comme suit :  
  
```  
Text\0Driver=TEXT.DLL\0Setup=TXTSETUP.DLL\0FileUsage=1\0  
FileExtns=*.txt,*.csv\0\0  
```  
  
 Supposons qu’un pilote pour SQL Server ne dispose pas d’une DLL d’installation distinct et n’a pas de mots clés n’importe quel attribut de pilote. Le *lpszDriver* argument pour ce pilote peut être comme suit :  
  
```  
SQL Server\0Driver=SQLSRVR.DLL\0\0  
```  
  
 Après avoir **SQLInstallDriverEx** récupère des informations sur le pilote à partir de la *lpszDriver* argument, il ajoute la description de pilote à la section [ODBC Drivers] de l’entrée de fichier Odbcinst.ini dans le système plus d’informations. Ensuite, il crée une section intitulée avec description du pilote et ajoute les chemins d’accès complets de la DLL du pilote et de la DLL d’installation. Enfin, elle retourne le chemin d’accès du répertoire cible de l’installation, mais ne copie pas les fichiers de pilote à celui-ci. Le programme appelant doit copier les fichiers de pilote dans le répertoire cible.  
  
 **SQLInstallDriverEx** incrémente le décompte d’utilisation de composant pour le pilote installé par 1. Si une version du pilote existe déjà, mais le nombre d’utilisations de composant pour le pilote n’existe pas, la nouvelle valeur de nombre de l’utilisation de composant est définie à 2.  
  
 Le programme d’installation d’application est responsable de la copier physiquement le fichier de pilote et de maintenir le décompte d’utilisation de fichier. Si le fichier de pilote n’a pas encore été installé, le programme d’installation d’application doit copier le fichier dans le *lpszPathIn* chemin d’accès et créer le décompte d’utilisation de fichier. Si le fichier a déjà été installé, le programme d’installation simplement incrémente le décompte d’utilisation de fichier et retourne le chemin d’accès de l’installation précédente dans le *lpszPathOut* argument.  
  
> [!NOTE]  
>  Pour plus d’informations sur les compteurs d’utilisation de composant et des compteurs d’utilisation de fichier, consultez [nombre d’utilisations](../../../odbc/reference/install/usage-counting.md).  
  
 Si une version antérieure du fichier du pilote a été précédemment installée par l’application, le pilote doit être désinstallé et réinstallé, afin que le nombre d’utilisations de composant pilote est valide. **SQLConfigDriver** (avec un *fréquents* de ODBC_REMOVE_DRIVER) doit tout d’abord être appelée, puis **SQLRemoveDriver** doit être appelé pour décrémenter le décompte d’utilisation de composant. **SQLInstallDriverEx** doit ensuite être appelée pour réinstaller le pilote, d’incrémenter le décompte d’utilisation de composant. Le programme d’installation d’application doit remplacer l’ancien fichier avec le nouveau fichier. Le décompte d’utilisation de fichiers restent les mêmes, et toute autre application qui a utilisé l’ancien fichier de version utilise désormais la version plus récente.  
  
> [!NOTE]  
>  Si le pilote a été installé précédemment et **SQLInstallDriverEx** est appelée pour installer le pilote dans un autre répertoire, la fonction renverra TRUE, mais *lpszPathOut* inclura le répertoire où le pilote a déjà été installé. Il n’inclut pas le répertoire entré dans le *lpszDriver* argument.  
  
 La longueur du chemin dans *lpszPathOut* dans **SQLInstallDriverEx** permettant à un processus d’installation en deux phases, pour une application de déterminer ce que *cbPathOutMax* doit être par appel **SQLInstallDriverEx** avec un *fréquents* du mode ODBC_INSTALL_INQUIRY. Cela retourne le nombre total d’octets disponibles dans le *pcbPathOut* mémoire tampon. **SQLInstallDriverEx** peut ensuite être appelée avec un *fréquents* de ODBC_INSTALL_COMPLETE et *cbPathOutMax* argument défini à la valeur de la *pcbPathOut*mémoire tampon, ainsi que le caractère de fin de la valeur null.  
  
 Si vous choisissez de ne pas utiliser le modèle en deux phases pour **SQLInstallDriverEx**, vous devez définir *cbPathOutMax*, qui définit la taille du stockage pour le chemin d’accès du répertoire cible, à la valeur _MAX_PATH, en tant que défini dans Stdlib.h, pour empêcher la troncation.  
  
 Lorsque *fréquents* est ODBC_INSTALL_COMPLETE, **SQLInstallDriverEx** n’autorise pas *lpszPathOut* null (ou *cbPathOutMax* être (0). Si *fréquents* est ODBC_INSTALL_COMPLETE, FALSE est retournée lorsque le nombre d’octets à retourner est supérieur ou égal à *cbPathOutMax*, avec le résultat que la troncation se produit.  
  
 Après avoir **SQLInstallDriverEx** a été appelée et le programme d’installation d’application a copié le fichier de pilote (si nécessaire), le programme d’installation du pilote DLL doit appeler **SQLConfigDriver** pour définir la configuration pour le pilote.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Installation du Gestionnaire de pilotes|[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|
