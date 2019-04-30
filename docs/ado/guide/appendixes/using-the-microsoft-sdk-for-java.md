---
title: Utilisation du SDK Microsoft pour Java | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Java (Microsoft SDK for)
- Microsoft SDK for Java [ADO]
ms.assetid: 2d7cb5b5-8307-49dd-b07e-c07069bb1626
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ab4aaed1cfd661d38476c81f8bdc3dcab3aa0f88
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199749"
---
# <a name="using-the-microsoft-sdk-for-java"></a>Utilisation du SDK Microsoft pour Java

> [!IMPORTANT]
> Microsoft prend plus en charge de Visual J ++ en janvier 2004.

Le SDK Microsoft pour Java est le kit de développement pour l’environnement de Microsoft Internet Explorer. Outils, des informations et des exemples sont fournis pour vous aider à développer des programmes Java et applets selon JDK 1.1 et la machine virtuelle de Microsoft Win32 (Microsoft VM). Le SDK Microsoft pour Java n’est pas lié à Microsoft Visual J ++. Pour télécharger ce SDK, cliquez ici.  
  
 L’utilitaire Jactivex.exe génère des classes à partir d’une bibliothèque de types, mais peut uniquement être appelée sur la ligne de commande. Cette fonctionnalité n’est pas intégrée à l’environnement de développement Visual J ++. Contrairement aux classes générées par l’Assistant Bibliothèque de types Java, vous pouvez entrer dans les wrappers de classe créés par le Kit de développement. Cela est utile pour le débogage dont votre code utilise les classes de wrapper ADO.  
  
 Ce mécanisme lit la bibliothèque de types ADO et génère des classes que vous pouvez instancier au sein de votre application. Il génère ces classes à l’emplacement suivant : \\< répertoire windows\>\Java\trustlib\msado15.  
  
 Création d’une application ADO dans Java à l’aide du SDK Microsoft pour Java est fondamentalement identique, du point de vue du code source, à l’aide de l’Assistant Bibliothèque de types Java. Pour l’exemple de code, consultez [Wrappers de classe Java ADO](../../../ado/guide/appendixes/ado-java-class-wrappers.md). La seule différence est dans la manière dont vous générez les classes wrapper en premier lieu, comme illustré dans les étapes suivantes.  
  
### <a name="to-create-an-ado-project-with-the-microsoft-sdk-for-java"></a>Pour créer un projet ADO avec le SDK Microsoft pour Java  
  
1.  Exécutez la commande suivante à une invite de commandes. Vous devez définir le chemin d’accès pour inclure le SDK Microsoft pour le répertoire Bin de Java, ou exécutez la commande à partir de cet emplacement. En règle générale, le SDK Microsoft pour Java est installé dans le même emplacement que Visual Studio. Il s’agit d’une instruction de commande unique.  
  
    ```java
    \<path to DevStudio>\<path to Java SDK>\bin\JactiveX.exe /javatlb "C:\program files\common files\system\ado\msado15.dll"  
    ```  
  
2.  Exécutez la commande suivante pour compiler les classes générées. Le commutateur/g : t active la génération de symboles de débogage afin que vous puissiez suivre la. Symboles de Java. Supprimer que les versions release.  
  
    ```java
    jvc /g:t c:\<windows>\Java\trustlib\msado15\*.Java  
    ```  
  
3.  Pour utiliser ces fichiers, ouvrez votre projet dans Visual J ++. À partir de la **projet** menu, choisissez **ajouter au projet**. Sélectionnez **fichiers**, puis ajoutez tous les. Fichiers JAVA générés dans le répertoire trustlib\msado15 à votre projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Wrappers de classe Java ADO](../../../ado/guide/appendixes/ado-java-class-wrappers.md)   
