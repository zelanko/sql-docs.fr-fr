---
title: Programme d’installation (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 08/31/2016
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], setup program
ms.assetid: 9cc5d75d-b293-41e5-927c-10f4af2e7af1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b89cae70db65bd2aa54b8e9789a5c2b35696923e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296149"
---
# <a name="setup-program"></a>Programme d’installation
> **REMARQUE:** En commençant par Windows XP et Windows Server 2003, **ODBC est inclus dans le système d’exploitation Windows**. Vous ne devez installer explicitement ODBC que sur les versions antérieures de Windows.  
  
 L’utilisateur exécute le programme de configuration pour démarrer le processus de configuration. Le programme d’installation est écrit par l’application ou le développeur de pilote. En plus d’installer des composants ODBC, il peut installer d’autres logiciels. Par exemple, les développeurs d’applications peuvent utiliser le même programme d’installation à la fois pour installer des composants ODBC et pour installer leurs applications.  
  
 Les développeurs peuvent écrire le programme de configuration à partir de zéro, en utilisant le Microsoft® Windows® les utilitaires d’installation SDK ou des logiciels de configuration d’autres fournisseurs. Cela donne à ces développeurs un contrôle complet sur l’apparence et la sensation du programme de configuration. Le programme d’installation peut être écrit pour installer des logiciels supplémentaires, tels qu’une application ODBC. Pour plus d’informations sur les utilitaires d’installation Windows SDK, consultez la documentation Windows SDK.  
  
 La quantité d’installation réellement effectuée par le programme d’installation dépend des fonctions qu’il appelle dans l’installateur DLL. L’installateur DLL contient des fonctions pour installer des composants ODBC individuels. Le programme d’installation appelle simplement **SQLInstallDriverManager**, **SQLInstallDriverEx**, ou **SQLInstallTranslatorEx** dans l’installateur DLL pour récupérer le chemin de l’annuaire dans lequel le composant doit être installé et pour ajouter des informations sur le composant au registre. Ces fonctions ne copient pas réellement les fichiers; le programme d’installation le fait en utilisant l’information dans les arguments de ces fonctions.  
  
 L’installateur DLL contient également des fonctions pour supprimer les composants ODBC. Le programme d’installation appelle **SQLRemoveDriverManager**, **SQLRemoveDriver**, ou **SQLRemoveTranslator** dans l’installateur DLL pour décérer le nombre d’utilisation d’un composant dans le registre et, si le nouveau nombre d’utilisation du composant tombe à 0, supprimer toutes les informations sur le composant du registre. Ces fonctions ne suppriment pas réellement les fichiers pour le composant; le programme d’installation le fait si le nouveau nombre d’utilisation tombe à 0.
