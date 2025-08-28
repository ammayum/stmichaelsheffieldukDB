# stmichaelsheffieldukDB
Maria DB used
-- site contents
CREATE TABLE IF NOT EXISTS site_contents (
  section VARCHAR(100) NOT NULL,
  content LONGTEXT NOT NULL,  -- JSON string
  updated_at DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (section)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- members
CREATE TABLE IF NOT EXISTS members (
  id INT NOT NULL AUTO_INCREMENT,
  name VARCHAR(150) NOT NULL,
  email VARCHAR(190) NOT NULL,
  phone VARCHAR(50),
  message TEXT,
  status ENUM('pending','approved','declined') NOT NULL DEFAULT 'pending',
  created_at DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (id),
  KEY idx_status_created (status, created_at)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- sessions table is auto-created by express-mysql-session if not present;
-- if you need manual:
-- CREATE TABLE `sessions` (`session_id` varchar(128) COLLATE utf8mb4_bin NOT NULL, `expires` int(11) unsigned NOT NULL, `data` mediumtext COLLATE utf8mb4_bin, PRIMARY KEY (`session_id`)) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_bin;
