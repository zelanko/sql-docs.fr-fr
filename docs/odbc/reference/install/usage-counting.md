---
title: Nombre d’utilisations | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- usage counts [ODBC]
- file usage counts [ODBC]
- installing ODBC components [ODBC], usage counts
- subkeys [ODBC], usage counts
ms.assetid: 0678aee9-8256-463c-89dd-77b1a0dfdd60
author: MightyPen
ms.author: genemi
ms.openlocfilehash: edf9976dd3e5d890b46919808e896a8e81a0cd93
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093792"
---
# <a name="usage-counting"></a>Nombre d’utilisations
> [!NOTE]  
>  ODBC à partir de Windows XP et Windows Server 2003, est inclus dans le système d’exploitation Windows. Vous devez explicitement uniquement installer ODBC dans les versions antérieures de Windows.  
  
 Deux types de compteurs d’utilisation sont conservées dans le Registre pour chaque composant : un nombre d’utilisations de composant et un ou plusieurs compteurs d’utilisation de fichier facultatif. Le programme d’installation permet du décompte d’utilisation de composant DLL mettre à jour les entrées de Registre. Il est stocké dans la valeur UsageCount sous le niveau principal ODBC, pilote et les sous-clés de translator. Pour le format de la valeur UsageCount et plus d’informations sur ces sous-clés, consultez [les entrées de Registre pour les composants ODBC](../../../odbc/reference/install/registry-entries-for-odbc-components.md).  
  
 Lors de l’installation d’un composant, le programme d’installation DLL crée une sous-clé pour celle-ci et les définit les données pour la valeur UsageCount dans cette sous-clé à 1. Lorsque le composant est installé à nouveau, le programme d’installation DLL incrémente le décompte d’utilisation. Lorsque le composant est supprimé, la décrémente DLL du programme d’installation le décompte d’utilisation. Si le décompte d’utilisation tombe à 0, le programme d’installation DLL supprime la sous-clé pour le composant.  
  
> [!CAUTION]  
>  Une application physiquement ne supprimez pas les fichiers de gestionnaire de pilotes lorsque le nombre d’utilisations de composant et le décompte d’utilisation de fichier atteint zéro.  
  
 Nombres de vous aider à déterminer quand un fichier doit réellement être copié ou supprimé en tant que l’utilisation du fichier opposition à incrémenter ou décrémenter le décompte d’utilisation. Ceci est important, car les composants ODBC et par conséquent, les fichiers dans les composants ODBC, sont partagées et peuvent être installés ou supprimés par une variété d’applications. L’application peut supprimer les fichiers de pilote et le convertisseur si le nombre d’utilisations de composant et le décompte d’utilisation de fichier atteint zéro. Fichiers du Gestionnaire de pilotes ne doit pas, toutefois, être supprimé lorsque le nombre d’utilisations de composant et le décompte d’utilisation de fichier ont atteint zéro, car ces fichiers peuvent être utilisés par d’autres applications qui n’ont pas incrémenté le décompte d’utilisation de fichier.  
  
> [!NOTE]  
>  Nombre d’utilisations de fichier est facultatifs dans Microsoft® WindowsNT®/Windows 2000.  
  
 Nombre d’utilisations de fichier est gérées par le programme d’installation après avoir appelé **SQLInstallDriverManager**, **SQLInstallDriverEx**, **SQLInstallTranslatorEx**, **SQLRemoveDriverManager**, **SQLRemoveDriver**, ou **SQLRemoveTranslator**.  
  
 Lors de l’installation d’un composant, le programme d’installation ou le programme d’installation DLL crée une valeur sous la clé suivante pour chaque fichier dans ce composant n’est pas déjà sur le système :  
  
> [!NOTE]  
>  HKEY_LOCAL_MACHINE  
>   
>  LOGICIEL  
>   
>  Microsoft  
>   
>  Windows  
>   
>  CurrentVersion  
>   
>  SharedDlls  
  
 Il définit les données pour ces valeurs sur 1 et copie le fichier dans le système. Lorsque le composant est installé à nouveau, le programme d’installation ou la DLL d’installation incrémente le nombre d’utilisations. Lorsque le composant est supprimé, la décrémente DLL d’installation programme ou le programme d’installation de la fréquence d’utilisation. Si n’importe quel nombre d’utilisations tombe à 0, le programme d’installation ou la DLL d’installation supprime la valeur pour le fichier et, si le composant est un pilote ou un traducteur, supprime le fichier. Fichiers du Gestionnaire de pilotes ne doivent pas être supprimés.  
  
 Le format de la valeur de nombre de l’utilisation de fichier est affiché dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|*chemin d’accès complet*|REG_DWORD|*nombre*|  
  
 Par exemple, supposons qu’un pilote pour Informix utilise les fichiers Infrmx32.dll et Infrmx32.hlp et supposons que ce pilote a été installé à deux reprises. Les valeurs sous la sous-clé SharedDlls pour le pilote Informix se présente comme suit :  
  
```  
C:\WINDOWS\SYSTEM32\INFRMX32.DLL : REG_DWORD : 0x2  
C:\WINDOWS\SYSTEM32\INFRMX32.HLP : REG_DWORD : 0x2  
```
