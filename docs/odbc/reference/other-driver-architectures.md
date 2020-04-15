---
title: Autres architectures de conducteur (en anglais) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae047fe8014b806d3bda8b0513521b4ddda072a7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280529"
---
# <a name="other-driver-architectures"></a>Autres architectures de pilote
Certains conducteurs de l’ODBC ne sont pas strictement conformes à l’architecture décrite précédemment. C’est peut-être parce que les conducteurs exécutent des tâches autres que celles d’un conducteur traditionnel de l’ODBC, ou ne sont pas des conducteurs au sens normal.  
  
## <a name="driver-as-a-middle-component"></a>Pilote comme composant moyen  
 Le conducteur de l’ODBC peut résider entre le gestionnaire de conducteur et un ou plusieurs autres conducteurs de l’ODBC. Lorsque le conducteur au milieu est capable de travailler avec plusieurs sources de données, il agit comme un répartiteur d’appels ODBC (ou des appels traduits de manière appropriée) à d’autres modules qui accèdent réellement aux sources de données. Dans cette architecture, le conducteur au milieu prend une partie du rôle d’un Driver Manager.  
  
 Un autre exemple de ce genre de conducteur est un programme d’espionnage pour ODBC, qui intercepte et copie les fonctions ODBC étant envoyés entre le gestionnaire de conducteur et le conducteur. Cette couche peut être utilisée pour émuler un pilote ou une application. Pour le gestionnaire de conducteur, la couche semble être le conducteur; pour le conducteur, la couche semble être le gestionnaire de conducteur.  
  
## <a name="heterogeneous-join-engines"></a>Moteurs de jointure hétérogènes  
 Certains conducteurs D’ODBC sont construits sur un moteur de requête pour effectuer des jointures hétérogènes. Dans une architecture d’un moteur de jointure hétérogène (voir l’illustration suivante), le conducteur apparaît à l’application comme un conducteur, mais semble à un autre cas du gestionnaire de conducteur comme une application. Ce conducteur traite une jointure hétérogène de l’application en appelant des instructions SQL distinctes dans les pilotes pour chaque base de données jointe.  
  
 ![Architecture d'un moteur de jointure hétérogène](../../odbc/reference/media/fig3-4.gif "fig3-4")  
  
 Cette architecture fournit une interface commune pour l’application d’accéder aux données de différentes bases de données. Il peut utiliser un moyen commun de récupérer les métadonnées, telles que des informations sur les colonnes spéciales (identificateurs de ligne), et il peut appeler des fonctions de catalogue communes pour récupérer les informations du dictionnaire de données. En appelant la fonction ODBC **SQLStatistics**, par exemple, l’application peut récupérer des informations sur les index sur les tableaux à joindre, même si les tables sont sur deux bases de données distinctes. Le processeur de requête n’a pas à se soucier de la façon dont les bases de données stockent les métadonnées.  
  
 L’application a également un accès standard aux types de données. ODBC définit les types de données SQL courants auxquels les types de données spécifiques au DBMS sont cartographiés. Une application peut appeler **SQLGetTypeInfo** pour récupérer des informations sur les types de données sur différentes bases de données.  
  
 Lorsque l’application génère une déclaration de jointure hétérogène, le processeur de requête dans cette architecture analyse la déclaration SQL, puis génère des relevés SQL distincts pour chaque base de données à joindre. En utilisant des métadonnées sur chaque pilote, le processeur de requête peut déterminer la jointure la plus efficace et intelligente. Par exemple, si l’instruction rejoint deux tables sur une base de données avec une table sur une autre base de données, le processeur de requête peut rejoindre les deux tables sur une base de données avant de rejoindre le résultat avec la table de l’autre base de données.  
  
## <a name="odbc-on-the-server"></a>ODBC sur le serveur  
 Les pilotes ODBC peuvent être installés sur un serveur afin qu’ils puissent être utilisés par des applications sur n’importe laquelle d’une série de machines clientes. Dans cette architecture (voir l’illustration suivante), un Driver Manager et un seul pilote ODBC sont installés sur chaque client, et un autre Driver Manager et une série de pilotes ODBC sont installés sur le serveur. Cela permet à chaque client d’accéder à une variété de pilotes utilisés et entretenus sur le serveur.  
  
 ![Architecture des pilotes ODBC sur un serveur](../../odbc/reference/media/fig3-5.gif "Fig3-5")  
  
 Un avantage de cette architecture est la maintenance et la configuration efficaces des logiciels. Les pilotes n’ont qu’à être mis à jour en un seul endroit : sur le serveur. En utilisant des sources de données système, les sources de données peuvent être définies sur le serveur pour une utilisation par tous les clients. Les sources de données n’ont pas besoin d’être définies sur le client. La mise en commun des connexions peut être utilisée pour rationaliser le processus par lequel les clients se connectent à des sources de données.  
  
 Le conducteur sur le client est généralement un très petit conducteur qui transfère l’appel Driver Manager au serveur. Son empreinte peut être significativement plus petite que les pilotes ODBC entièrement fonctionnels sur le serveur. Dans cette architecture, les ressources client peuvent être libérées si le serveur a plus de puissance de calcul. En outre, l’efficacité et la sécurité de l’ensemble du système peuvent être améliorées en installant des serveurs de sauvegarde et en effectuant l’équilibrage de charge pour optimiser l’utilisation du serveur.
