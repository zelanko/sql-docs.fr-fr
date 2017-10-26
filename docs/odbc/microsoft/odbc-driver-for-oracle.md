---
title: Pilote ODBC pour Oracle | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC]
- ODBC driver for Oracle [ODBC], about ODBC driver for Oracle
- Oracle data access [ODBC]
ms.assetid: 937e0662-8b1d-44f7-b077-4015c6605b2c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e66dd7ed6406287c0fb4e6722d8b5915428f705b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-driver-for-oracle"></a>Pilote ODBC pour Oracle
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Microsoft® ODBC Driver for Oracle permet de connecter votre application compatible ODBC à une base de données Oracle. Le pilote ODBC pour Oracle est conforme à la spécification de la connectivité ODBC (Open Database) décrite dans la *de référence du programmeur ODBC*. Il autorise l’accès aux packages de PL/SQL, une intégration XA/DTC et accès d’Oracle à partir de dans Internet Information Services (IIS).  
  
 Oracle SGBDR est un système de gestion de base de données relationnelle multi-utilisateur qui s’exécute avec divers systèmes d’exploitation de station de travail et ses. Les ordinateurs compatibles IBM exécutant Microsoft Windows peuvent communiquer avec les serveurs de base de données Oracle sur un réseau. Réseaux pris en charge incluent Microsoft LAN Manager, NetWare, VINES, DECnet et n’importe quel réseau qui prend en charge de TCP/IP.  
  
 Le pilote ODBC pour Oracle permet à une application à accéder aux données dans une base de données Oracle via l’interface ODBC. Le pilote peut accéder à des bases de données Oracle locales ou il peut communiquer avec le réseau via SQL * Net. Le diagramme suivant détaille cette architecture de l’application et le pilote.  
  
 ![Pilote ODBC pour Oracle application &#47; architecture du pilote](../../odbc/microsoft/media/orcdrvsdkarch.gif "OrcDrvSDKArch")  
  
 Le pilote ODBC pour Oracle est conforme aux API de mise en conformité au niveau 1 et SQL conformité au niveau de base. Il prend également en charge certaines fonctions dans les API de mise en conformité au niveau 2 et la plupart de la grammaire dans les niveaux de conformité Core et SQL étendue. Le pilote est conforme à ODBC 2.5 et prend en charge les systèmes 32 bits. Oracle 7.3 x est prise en charge complète ; Oracle8 prend en charge limitée. Le pilote ODBC pour Oracle ne prend pas en charge les nouveaux types de données Oracle8 : types de données Unicode, BLOB, CLOB, et ainsi de suite, ni nouveau modèle d’Oracle d’objet relationnel. Pour plus d’informations sur les types de données pris en charge, consultez [pris en charge les Types de données](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md) dans ce guide.  
  
 Pour accéder aux données Oracle, les composants suivants sont requis :  
  
-   Le pilote ODBC pour Oracle  
  
-   Une base de données Oracle SGBDR  
  
-   Logiciel Client Oracle  
  
 En outre, pour les connexions à distance :  
  
-   Un réseau qui connecte les ordinateurs qui exécutent le pilote et la base de données. Le réseau doit prendre en charge SQL * Net de connexions.  
  
## <a name="component-documentation"></a>Documentation des composants  
 Ce guide contient des informations détaillées sur la configuration et configurer le pilote Microsoft ODBC pour Oracle et ajout de la fonctionnalité de programmation. Il contient également des documents de référence technique.  
  
 Pour plus d’informations concernant le comportement du produit Oracle spécifique, consultez la documentation qui accompagne le produit d’Oracle.  
  
 Pour plus d’informations sur la configuration ou la configuration du pilote Microsoft ODBC pour Oracle à l’aide de l’administrateur de Source de données ODBC, consultez le [administrateur de sources de données ODBC](../../odbc/admin/odbc-data-source-administrator.md) documentation.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Pilote ODBC pour le Guide de l’utilisateur Oracle](../../odbc/microsoft/odbc-driver-for-oracle-user-s-guide.md)  
  
-   [Pilote ODBC pour la référence du programmeur Oracle](../../odbc/microsoft/odbc-driver-for-oracle-programmer-s-reference.md)

