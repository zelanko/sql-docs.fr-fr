---
description: Programme d’installation
title: Programme d’installation | Microsoft Docs
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
ms.openlocfilehash: 4cd4858214ff084a037002abd3bd34035160496b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421323"
---
# <a name="setup-program"></a>Programme d’installation
> **Remarque :** À compter de Windows XP et de Windows Server 2003, **ODBC est inclus dans le système d’exploitation Windows**. Vous devez uniquement installer explicitement ODBC sur les versions antérieures de Windows.  
  
 L’utilisateur exécute le programme d’installation pour démarrer le processus d’installation. Le programme d’installation est écrit par le développeur de l’application ou du pilote. Outre l’installation des composants ODBC, il peut installer d’autres logiciels. Par exemple, les développeurs d’applications peuvent utiliser le même programme d’installation pour installer les composants ODBC et installer leurs applications.  
  
 Les développeurs peuvent écrire le programme d’installation à partir de zéro à l’aide des utilitaires d’installation du kit de développement logiciel (SDK) Microsoft® Windows® ou d’autres fournisseurs. Cela permet aux développeurs de contrôler entièrement l’apparence du programme d’installation. Le programme d’installation peut être écrit pour installer des logiciels supplémentaires, comme une application ODBC. Pour plus d’informations sur les utilitaires d’installation SDK Windows, consultez la documentation SDK Windows.  
  
 La partie de l’installation effectuée par le programme d’installation dépend des fonctions qu’il appelle dans la DLL du programme d’installation. La DLL du programme d’installation contient des fonctions permettant d’installer des composants ODBC individuels. Le programme d’installation appelle simplement **SQLInstallDriverManager**, **SQLInstallDriverEx**ou **SQLInstallTranslatorEx** dans la dll du programme d’installation pour récupérer le chemin d’accès du répertoire dans lequel le composant doit être installé et pour ajouter des informations sur le composant au registre. Ces fonctions ne copient pas réellement les fichiers ; pour ce faire, le programme d’installation utilise les informations contenues dans les arguments de ces fonctions.  
  
 La DLL du programme d’installation contient également des fonctions permettant de supprimer des composants ODBC. Le programme d’installation appelle **SQLRemoveDriverManager**, **SQLRemoveDriver**ou **SQLRemoveTranslator** dans la dll du programme d’installation pour décrémenter le nombre d’utilisations d’un composant dans le registre et, si le nouveau nombre d’utilisations du composant est égal à 0, supprimez toutes les informations sur le composant du Registre. Ces fonctions ne suppriment pas réellement les fichiers pour le composant ; le programme d’installation effectue cette procédure si le nouveau compte d’utilisation est égal à 0.
