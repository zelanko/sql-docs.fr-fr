---
title: Prise en main de SSMA pour Sybase Console (SybaseToSQL) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Launching SSMA Console
- Sybase Console,Output Conventions
- Sybase Console,Procedure for Using Console
ms.assetid: 43219dbe-bcfa-427d-9242-f07b1455f15f
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 239b7a8f4dbc3069e67d680b319bf426a0f917e6
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="getting-started-with-ssma-for-sybase-console-sybasetosql"></a>Prise en main de SSMA pour Sybase Console (SybaseToSQL)
Cette section décrit la procédure pour lancer et commencer à l’application de console Sybase. Dans la liste, qu’elle contient, sont les conventions utilisées dans une fenêtre de sortie de Console de SSMA classique.  
  
## <a name="launching-ssma-console"></a>Lancer la Console SSMA  
Utilisez les étapes suivantes pour démarrer l’application de console SSMA :  
  
1.  Accédez à démarrer et pointez sur tous les programmes.  
  
2.  Cliquez sur le **SQL Server Migration Assistant pour Sybase invite de commandes** contextuel.  
  
    Il affiche le menu de l’utilisation de SSMA Console et `(/? Help)`, pour vous aider à démarrer avec l’application console.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Procédure d’utilisation de la Console SSMA  
Une fois que la console est lancée correctement sur votre système Windows, vous pouvez utiliser les étapes suivantes pour travailler dessus :  
  
1.  Configurer la Console de SSMA via les fichiers de script. Pour plus d’informations sur cette section, consultez [création de fichiers de Script &#40; SybaseToSQL &#41; ](../../ssma/sybase/creating-script-files-sybasetosql.md) .  
  
2.  [Création de fichiers de la valeur de la Variable &#40; SybaseToSQL &#41;](../../ssma/sybase/creating-variable-value-files-sybasetosql.md)  
  
3.  [Créer les fichiers de connexion de serveur &#40; SybaseToSQL &#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md)  
  
4.  [L’exécution de la Console SSMA &#40; SybaseToSQL &#41; ](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md) selon les besoins de votre projet  
  
Fonctionnalités supplémentaires :  
  
1.  [Spécifiez un mot de passe](http://msdn.microsoft.com/en-us/9b6a70f9-6840-4140-a059-bb7bd7ccc67c) et exporter / importer sur d’autres ordinateurs de la fenêtre  
  
2.  [Générer des rapports](http://msdn.microsoft.com/en-us/19278f6a-6d58-4867-9d71-c6228040466e) pour afficher le code xml détaillé rapports pour évaluation /conversion et migration des données de sortie. Rapports d’erreur détaillé peuvent également être générées pour les commandes d’actualisation et la synchronisation.  
  
## <a name="ssma-console-output-conventions"></a>Conventions de sortie de Console SSMA  
Lors de l’exécution des commandes de script SSMA et des options, le programme de console affiche les résultats et les messages (information, erreur, etc.) à l’utilisateur sur la console ou si nécessaire, redirige vers un fichier de sortie xml. Chaque type de message dans la sortie est signalé par une couleur unique. Par exemple, le message de couleur blanche indique les commandes du fichier de script. celui de couleur verte représente une invite de commandes pour l’entrée d’utilisateur et ainsi de suite.  
  
![SSMAConsoleOutput_Sybase](../../ssma/sybase/media/ssmaconsoleoutput_sybase.JPG "SSMAConsoleOutput_Sybase")  
  
Interprétation de couleur de la sortie de console dans le tableau suivant :  
  
|Color| Description|  
|---------|---------------|  
|Rouge|Erreur irrécupérable lors de l’exécution|  
|Gris|Cachet de date et heure, le message à l’utilisateur|  
|White|Commandes du fichier de script, le type de message|  
|Jaune|Avertissement|  
|Vert|Invite d’entrée d’utilisateur|  
|Cyan|Début, fin et le résultat d’une opération|  
  
## <a name="see-also"></a>Voir aussi  
[L’installation de SSMA pour Sybase &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
  

