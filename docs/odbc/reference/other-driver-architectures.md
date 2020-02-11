---
title: Autres architectures de pilote | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- drivers [ODBC], heterogeneous join engines
- drivers [ODBC], ODBC on the server
- ODBC architecture [ODBC], drivers
- heterogeneous join engines[ODBC]
- drivers [ODBC], middle component
ms.assetid: 1cad06ee-5940-4361-8d01-7d850db1dd66
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8dbfb09a261d7499e07137b7ed830d5a5b92dc73
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086011"
---
# <a name="other-driver-architectures"></a>Autres architectures de pilote
Certains pilotes ODBC ne sont pas strictement conformes à l’architecture décrite précédemment. Cela peut être dû au fait que les pilotes exécutent des tâches autres que celles d’un pilote ODBC traditionnel, ou qu’il ne s’agit pas de pilotes dans le sens normal.  
  
## <a name="driver-as-a-middle-component"></a>Pilote en tant que composant du milieu  
 Le pilote ODBC peut résider entre le gestionnaire de pilotes et un ou plusieurs autres pilotes ODBC. Lorsque le pilote au milieu peut fonctionner avec plusieurs sources de données, il joue le rôle de répartiteur d’appels ODBC (ou d’appels traduits de manière appropriée) à d’autres modules qui accèdent effectivement aux sources de données. Dans cette architecture, le pilote au milieu prend le rôle d’un gestionnaire de pilotes.  
  
 Un autre exemple de ce type de pilote est un programme Spy pour ODBC, qui intercepte et copie les fonctions ODBC envoyées entre le gestionnaire de pilotes et le pilote. Cette couche peut être utilisée pour émuler un pilote ou une application. Pour le gestionnaire de pilotes, la couche semble être le pilote ; pour le pilote, la couche semble être le gestionnaire de pilotes.  
  
## <a name="heterogeneous-join-engines"></a>Moteurs de jointure hétérogènes  
 Certains pilotes ODBC sont basés sur un moteur de requête pour l’exécution de jointures hétérogènes. Dans une architecture d’un moteur de jointure hétérogène (Voir l’illustration suivante), le pilote apparaît à l’application en tant que pilote, mais s’affiche dans une autre instance du gestionnaire de pilotes en tant qu’application. Ce pilote traite une jointure hétérogène à partir de l’application en appelant des instructions SQL distinctes dans les pilotes pour chaque base de données jointe.  
  
 ![Architecture d'un moteur de jointure hétérogène](../../odbc/reference/media/fig3-4.gif "fig3-4")  
  
 Cette architecture fournit une interface commune permettant à l’application d’accéder aux données à partir de différentes bases de données. Il peut utiliser une méthode courante pour récupérer des métadonnées, telles que des informations sur les colonnes spéciales (identificateurs de ligne), et il peut appeler des fonctions de catalogue courantes pour récupérer des informations de dictionnaire de données. En appelant la fonction ODBC **SQLStatistics**, par exemple, l’application peut récupérer des informations sur les index sur les tables à joindre, même si les tables se trouvent sur deux bases de données distinctes. Le processeur de requêtes n’a pas à se soucier de la façon dont les bases de données stockent les métadonnées.  
  
 L’application dispose également d’un accès standard aux types de données. ODBC définit les types de données SQL courants auxquels les types de données propres au SGBD sont mappés. Une application peut appeler **SQLGetTypeInfo** pour récupérer des informations sur des types de données sur différentes bases de données.  
  
 Lorsque l’application génère une instruction de jointure hétérogène, le processeur de requêtes dans cette architecture analyse l’instruction SQL, puis génère des instructions SQL distinctes pour chaque base de données à joindre. En utilisant les métadonnées de chaque pilote, le processeur de requêtes peut déterminer la jointure la plus efficace et intelligente. Par exemple, si l’instruction joint deux tables sur une base de données avec une table sur une autre base de données, le processeur de requêtes peut joindre les deux tables de la base de données avant de joindre le résultat à la table de l’autre base de données.  
  
## <a name="odbc-on-the-server"></a>ODBC sur le serveur  
 Les pilotes ODBC peuvent être installés sur un serveur de sorte qu’ils puissent être utilisés par des applications sur une série de machines clientes. Dans cette architecture (Voir l’illustration suivante), un gestionnaire de pilotes et un seul pilote ODBC sont installés sur chaque client, et un autre gestionnaire de pilotes et une série de pilotes ODBC sont installés sur le serveur. Cela permet à chaque client d’accéder à différents pilotes utilisés et maintenus sur le serveur.  
  
 ![Architecture des pilotes ODBC sur un serveur](../../odbc/reference/media/fig3-5.gif "FIG3-5")  
  
 L’un des avantages de cette architecture est l’efficacité de la maintenance et de la configuration des logiciels. Les pilotes doivent être mis à jour à un seul emplacement : sur le serveur. En utilisant des sources de données système, les sources de données peuvent être définies sur le serveur pour être utilisées par tous les clients. Les sources de données n’ont pas besoin d’être définies sur le client. Le regroupement de connexions peut être utilisé pour simplifier le processus par lequel les clients se connectent aux sources de données.  
  
 Le pilote sur le client est généralement un très petit pilote qui transfère l’appel du gestionnaire de pilotes au serveur. Son encombrement peut être considérablement plus petit que celui des pilotes ODBC entièrement fonctionnels sur le serveur. Dans cette architecture, les ressources client peuvent être libérées si le serveur dispose de davantage de puissance de calcul. En outre, l’efficacité et la sécurité de l’ensemble du système peuvent être améliorées en installant des serveurs de sauvegarde et en effectuant l’équilibrage de charge pour optimiser l’utilisation du serveur.
