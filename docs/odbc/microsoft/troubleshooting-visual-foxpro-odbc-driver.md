---
title: Résolution des problèmes (pilote ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set ANSI [ODBC]
- troubleshooting Visual FoxPro ODBC driver [ODBC]
- remote views [ODBC]
- multitiered views [ODBC]
- parameterized views [ODBC], Visual FoxPro ODBC driver
- fetches [ODBC], Visual FoxPro ODBC driver
- positioned updates [ODBC]
- background fetching [ODBC]
ms.assetid: fd478dd8-666a-4f0a-a2d6-b94e81cbbe4b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4eeb6210b9bce124e16a1b4e666dee03c1d992be
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67912387"
---
# <a name="troubleshooting-visual-foxpro-odbc-driver"></a>Résolution des problèmes (pilote ODBC Visual FoxPro)
Les sections suivantes expliquent comment améliorer les performances et résoudre les problèmes que vous pouvez rencontrer lors de l’utilisation du pilote ODBC Visual FoxPro.  
  
## <a name="accessing-parameterized-views"></a>Accès aux vues paramétrées  
 Vous ne pouvez pas accéder aux vues paramétrées dans une base de données Visual FoxPro à l’aide du pilote. Une vue paramétrable crée une clause WHERE dans l’instruction SQL **Select** de la vue qui limite les enregistrements téléchargés aux enregistrements qui remplissent les conditions de la clause WHERE créée à l’aide de la valeur fournie pour le paramètre. Étant donné que le pilote ne prend pas en charge le passage de paramètres à la vue, les tentatives d’accès à une vue paramétrée à l’aide du pilote échouent.  
  
 La valeur du paramètre peut être fournie au moment de l’exécution ou passée par programme à la vue.  
  
## <a name="accessing-remote-views"></a>Accès aux vues distantes  
 Vous ne pouvez pas accéder à des vues distantes dans une base de données Visual FoxPro à l’aide du pilote. Les vues distantes sont des vues qui accèdent à des données non-FoxPro ou à une combinaison de données FoxPro et non FoxPro. Pour accéder aux vues à distance, utilisez Visual FoxPro.  
  
## <a name="deleting-records"></a>Suppression d’enregistrements  
 Vous pouvez marquer les enregistrements à supprimer à l’aide du pilote, mais vous ne pouvez pas supprimer définitivement les enregistrements de la base de données. Pour supprimer définitivement des enregistrements d’une table, utilisez Visual FoxPro.  
  
## <a name="increasing-performance-using-background-fetching"></a>Amélioration des performances à l’aide de la récupération en arrière-plan  
 Vous pouvez améliorer les performances des extractions volumineuses à l’aide de la fonctionnalité de récupération en arrière-plan du pilote. La récupération en arrière-plan utilise un thread distinct pour extraire les données demandées à partir d’une source de données spécifique.  
  
 Vous pouvez utiliser la récupération en arrière-plan pour une source de données de l’une des manières suivantes :  
  
-   Cochez la case **récupérer des données en arrière-plan** dans la [boîte de dialogue installation de ODBC pour Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md).  
  
-   Utilisez le mot clé d’attribut BackgroundFetch dans votre chaîne de connexion.  
  
 Pour plus d’informations sur les mots clés d’attribut de chaîne de connexion, consultez [utilisation de chaînes de connexion](../../odbc/microsoft/using-connection-strings.md).  
  
## <a name="updating-multitiered-views"></a>Mise à jour des vues multicouches  
 Une vue à plusieurs niveaux est une vue basée sur une ou plusieurs vues plutôt que sur une table de base. Lorsque vous mettez à jour des données dans une vue multicouche, les mises à jour ne sont pas répercutées sur un niveau, jusqu’à la vue sur laquelle la vue de niveau supérieur est basée. les tables de base ne sont pas mises à jour.  
  
## <a name="using-data-definition-language-ddl-in-stored-procedures"></a>Utilisation du langage de définition de données (DDL) dans les procédures stockées  
 Vous ne pouvez pas utiliser DDL, tel que CREATE TABLE ou ALTER TABLE, dans les procédures stockées Visual FoxPro.  
  
 Pour plus d’informations sur le langage que vous pouvez utiliser dans les procédures stockées, consultez [prise en charge des règles, des déclencheurs, des valeurs par défaut et des procédures stockées](../../odbc/microsoft/support-rules-triggers-defaults-stored-procedures-visual-foxpro-odbc-driver.md).  
  
## <a name="using-positioned-updates"></a>Utilisation des mises à jour positionnées  
 Le pilote ne prend pas en charge les mises à jour positionnées. Utilisez la clause SQL WHERE pour identifier les lignes que vous souhaitez mettre à jour.  
  
## <a name="using-the-set-ansi-command"></a>Utilisation de la commande SET ANSI  
 Si vous êtes un développeur Visual FoxPro, vous devez savoir que le paramètre par défaut pour SET ANSI est activé pour le pilote, contrairement à un paramètre par défaut désactivé pour Visual FoxPro. La valeur par défaut de SET ANSI permet aux sources de données Visual FoxPro de se comporter de manière cohérente avec d’autres sources de données ODBC qui effectuent généralement des comparaisons exactes. Vous pouvez modifier le paramètre par défaut. Pour plus d’informations, consultez [SET ANSI](../../odbc/microsoft/set-ansi-command.md).
