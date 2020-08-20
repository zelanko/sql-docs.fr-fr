---
description: Nombre d’utilisations
title: Comptage de l’utilisation | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8e8c02aae51c47b13970a1824e3c0c9c417eb5f2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499692"
---
# <a name="usage-counting"></a>Nombre d’utilisations
> [!NOTE]  
>  À compter de Windows XP et de Windows Server 2003, ODBC est inclus dans le système d’exploitation Windows. Vous devez uniquement installer explicitement ODBC sur les versions antérieures de Windows.  
  
 Deux types de comptes d’utilisation sont conservés dans le registre pour chaque composant : un nombre d’utilisations de composants et un ou plusieurs nombres d’utilisations de fichiers facultatifs. Le nombre d’utilisations des composants aide la DLL du programme d’installation à conserver les entrées de registre. Elle est stockée dans la valeur UsageCount sous les sous-clés ODBC Core, Driver et translator. Pour obtenir le format de la valeur UsageCount et des informations supplémentaires sur ces sous-clés, consultez [entrées de Registre pour les composants ODBC](../../../odbc/reference/install/registry-entries-for-odbc-components.md).  
  
 Quand un composant est installé pour la première fois, la DLL du programme d’installation crée une sous-clé pour celui-ci et définit les données de la valeur UsageCount dans cette sous-clé sur 1. Une fois le composant installé, la DLL du programme d’installation incrémente le nombre d’utilisations. Lorsque le composant est supprimé, la DLL du programme d’installation décrémente le nombre d’utilisations. Si le nombre d’utilisations correspond à 0, la DLL du programme d’installation supprime la sous-clé du composant.  
  
> [!CAUTION]  
>  Une application ne doit pas supprimer physiquement les fichiers du gestionnaire de pilotes lorsque le nombre d’utilisations des composants et le nombre d’utilisations du fichier atteignent zéro.  
  
 Le nombre d’utilisations de fichiers permet de déterminer quand un fichier doit réellement être copié ou supprimé au lieu d’incrémenter ou de décrémenter le nombre d’utilisations. C’est important, car les composants ODBC et, par conséquent, les fichiers des composants ODBC, sont partagés et peuvent être installés ou supprimés par diverses applications. L’application peut supprimer les fichiers de pilote et de traducteur si le nombre d’utilisations des composants et le nombre d’utilisations du fichier atteignent zéro. Toutefois, les fichiers du gestionnaire de pilotes ne doivent pas être supprimés lorsque le nombre d’utilisations des composants et le nombre d’utilisations des fichiers ont atteint zéro, car ces fichiers peuvent être utilisés par d’autres applications qui n’ont pas incrémenté le nombre d’utilisations des fichiers.  
  
> [!NOTE]  
>  Les comptes d’utilisation de fichiers sont facultatifs dans Microsoft® WindowsNT®/Windows2000.  
  
 Le nombre d’utilisations de fichiers est géré par le programme d’installation après l’appel de **SQLInstallDriverManager**, **SQLInstallDriverEx**, **SQLInstallTranslatorEx**, **SQLRemoveDriverManager**, **SQLRemoveDriver**ou **SQLRemoveTranslator**.  
  
 Quand un composant est installé pour la première fois, le programme d’installation ou la DLL du programme d’installation crée une valeur sous la clé suivante pour chaque fichier de ce composant qui ne se trouve pas déjà sur le système :  
  
> [!NOTE]  
>  HKEY_LOCAL_MACHINE  
>   
>  LOGICIELLE  
>   
>  Microsoft  
>   
>  Windows  
>   
>  CurrentVersion  
>   
>  SharedDlls  
  
 Il définit les données pour ces valeurs sur 1 et copie le fichier sur le système. Une fois le composant installé à nouveau, le programme d’installation ou la DLL du programme d’installation incrémente le nombre d’utilisations. Lorsque le composant est supprimé, le programme d’installation ou la DLL du programme d’installation décrémente le nombre d’utilisations. Si le nombre d’utilisations est égal à 0, le programme d’installation ou la DLL du programme d’installation supprime la valeur du fichier et, si le composant est un pilote ou un convertisseur, supprime le fichier. Les fichiers du gestionnaire de pilotes ne doivent pas être supprimés.  
  
 Le format de la valeur du nombre d’utilisations de fichier est indiqué dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|*chemin d’accès complet*|REG_DWORD|*count*|  
  
 Par exemple, supposons qu’un pilote pour Informix utilise les fichiers Infrmx32.dll et Infrmx32. hlp, et supposons que ce pilote ait été installé deux fois. Les valeurs de la sous-clé SharedDlls pour le pilote Informix sont les suivantes :  
  
```  
C:\WINDOWS\SYSTEM32\INFRMX32.DLL : REG_DWORD : 0x2  
C:\WINDOWS\SYSTEM32\INFRMX32.HLP : REG_DWORD : 0x2  
```
