---
title: Correctifs logiciels Oracle | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], Oraclesoftware patches
- Oracle software patches [ODBC]
ms.assetid: 1275157b-f4e1-4c24-b273-c02555e261c2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: afd5a20d99692c1a623b13b53218f62c00cb218a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47845917"
---
# <a name="oracle-software-patches"></a>Correctifs logiciels Oracle
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Les correctifs pour les produits de serveur Oracle et de son composant de client sont nécessaires au bon fonctionnement de plusieurs produits et technologies Microsoft, y compris le pilote Microsoft ODBC pour Oracle, le fournisseur Microsoft OLE DB pour Oracle, Internet Information Services (IIS), Services de composants (ou Microsoft Transaction Server, si vous utilisez Windows NT), et ainsi de suite.  
  
> [!NOTE]  
>  Les instructions suivantes ne sont peut-être pas complètement précises, car le site FTP d’Oracle est susceptible de changer.  
  
### <a name="to-download-the-oracle-software-patches"></a>Pour télécharger les correctifs logiciels Oracle  
  
1.  Se connecter au site FTP public à ftp.oracle.com d’oracle. L’ID d’utilisateur est « anonymous » et le mot de passe est votre adresse de messagerie.  
  
2.  Accédez au répertoire suivant : /server/wgt_tech/server/windowsNT.  
  
3.  Pour télécharger des correctifs les plus pertinents pour Windows 95, Windows 98 et Windows NT/Windows 2000, accédez au sous-répertoire de votre version d’Oracle : 7.3 ou 8.0. Les deux sous-répertoires sont /73patchsets et /80patchsets.  
  
4.  Pour télécharger des correctifs pour la technologie de réseau d’Oracle, SQL * Net ou Net8, accédez au répertoire suivant : / réseau.  
  
 L’accès à ce site FTP à partir de votre navigateur Web peut ne pas fonctionner. Si vous rencontrez des problèmes, essayez d’utiliser un client FTP « traditionnel », ou utiliser l’invite de commandes DOS.  
  
> [!NOTE]  
>  Oracle corrige les bogues dans les versions actuelles et puis de les retrofits vers des versions antérieures à l’aide de correctifs logiciels, il est recommandé que vous téléchargez le dernier correctif logiciel disponible. Cela est particulièrement vrai pour les composants du Client de serveur Oracle. Si vous avez des questions sur l’installation de ces correctifs, contactez le support technique Oracle.
