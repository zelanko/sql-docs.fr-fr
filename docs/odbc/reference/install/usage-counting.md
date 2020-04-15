---
title: Comptage de l’utilisation (en anglais seulement) Microsoft Docs
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
ms.openlocfilehash: 8d516a591bfde47522c0ccfe08bd2bd706218e07
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296019"
---
# <a name="usage-counting"></a>Nombre d’utilisations
> [!NOTE]  
>  En commençant par Windows XP et Windows Server 2003, ODBC est inclus dans le système d’exploitation Windows. Vous ne devez installer explicitement ODBC que sur les versions antérieures de Windows.  
  
 Deux types de comptes d’utilisation sont maintenus dans le registre pour chaque composant : un compte d’utilisation des composants et un ou plusieurs comptes facultatifs d’utilisation des fichiers. Le nombre d’utilisation des composants aide l’installateur DLL à maintenir les entrées de registre. Il est stocké dans la valeur UseCount sous les sous-clés ODBC Core, driver et traducteur. Pour le format de la valeur UseCount et plus d’informations sur ces sous-clés, voir [Inscriptions de registre pour les composants ODBC](../../../odbc/reference/install/registry-entries-for-odbc-components.md).  
  
 Lorsqu’un composant est installé pour la première fois, l’installateur DLL crée un sous-clé pour elle et définit les données pour la valeur UseCount dans ce sous-clé à 1. Lorsque le composant est installé à nouveau, l’installateur DLL incréments le nombre d’utilisation. Lorsque le composant est enlevé, l’installateur DLL décrément le nombre d’utilisation. Si le nombre d’utilisation tombe à 0, l’installateur DLL supprime le sous-clé pour le composant.  
  
> [!CAUTION]  
>  Une application ne doit pas supprimer physiquement les fichiers Driver Manager lorsque l’utilisation des composants compte et que le nombre d’utilisation du fichier atteint zéro.  
  
 Les comptes d’utilisation des fichiers aident à déterminer quand un fichier doit effectivement être copié ou supprimé par opposition à l’augmentation ou à la décroissation du nombre d’utilisation. Ceci est important parce que les composants ODBC, et donc les fichiers dans les composants ODBC, sont partagés et peuvent être installés ou supprimés par une variété d’applications. L’application peut supprimer les fichiers conducteur et traducteur si le nombre d’utilisation des composants et le nombre d’utilisation du fichier atteignent zéro. Les fichiers Driver Manager ne doivent toutefois pas être supprimés lorsque le nombre d’utilisation des composants et le nombre d’utilisations des fichiers ont atteint zéro, car ces fichiers peuvent être utilisés par d’autres applications qui n’ont pas augmenté le nombre d’utilisation du fichier.  
  
> [!NOTE]  
>  Les comptes d’utilisation des fichiers sont facultatifs dans Microsoft® WindowsNT®/Windows2000.  
  
 Les comptes d’utilisation des fichiers sont maintenus par le programme d’installation après qu’il appelle **SQLInstallDriverManager**, **SQLInstallDriverEx**, **SQLInstallTranslatorEx**, **SQLRemoveDriverManager**, **SQLRemoveDriver**, ou **SQLRemoveTranslator**.  
  
 Lorsqu’un composant est installé pour la première fois, le programme d’installation ou l’installateur DLL crée une valeur sous la clé suivante pour chaque fichier de ce composant qui n’est pas déjà sur le système :  
  
> [!NOTE]  
>  HKEY_LOCAL_MACHINE  
>   
>  Logiciel  
>   
>  Microsoft  
>   
>  Windows  
>   
>  CurrentVersion  
>   
>  SharedDlls (en)  
  
 Il définit les données de ces valeurs à 1 et copie le fichier au système. Lorsque le composant est installé à nouveau, le programme d’installation ou l’installateur DLL incréments l’utilisation compte. Lorsque le composant est supprimé, le programme d’installation ou l’installateur DLL décrète le nombre d’utilisation. Si le nombre d’utilisation tombe à 0, le programme d’installation ou l’installateur DLL supprime la valeur du fichier et, si le composant est un pilote ou un traducteur, supprime le fichier. Les fichiers Driver Manager ne doivent pas être supprimés.  
  
 Le format de la valeur de comptage d’utilisation du fichier est indiqué dans le tableau suivant.  
  
|Nom|Type de données|Données|  
|----------|---------------|----------|  
|*plein chemin*|REG_DWORD|*count*|  
  
 Supposons, par exemple, qu’un conducteur d’Informix utilise les fichiers Infrmx32.dll et Infrmx32.hlp, et supposons que ce conducteur a été installé deux fois. Les valeurs sous le sous-clé SharedDlls pour le pilote Informix seraient les suivantes :  
  
```  
C:\WINDOWS\SYSTEM32\INFRMX32.DLL : REG_DWORD : 0x2  
C:\WINDOWS\SYSTEM32\INFRMX32.HLP : REG_DWORD : 0x2  
```
