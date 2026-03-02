ALTER TABLE PRODUCTLIST
ADD (PRICE NUMBER(10,2),
     DESCRIPTION VARCHAR2(250));

UPDATE PRODUCTLIST p
SET (p.PRICE, p.DESCRIPTION) = (
    SELECT s.PRICE, s.DESCRIPTION
    FROM STOREFRONT s
    WHERE s.PRODUCTCODE = p.PRODUCTCODE
)
WHERE EXISTS (
    SELECT 1
    FROM STOREFRONT s
    WHERE s.PRODUCTCODE = p.PRODUCTCODE
);

DROP TABLE STOREFRONT;

CREATE TABLE CHATLOG (
    CHATID NUMBER(3),
    RECEIVERID NUMBER(3),
    SENDERID NUMBER(3),
    DATESENT DATE,
    CONTENT VARCHAR2(250),
    CONSTRAINT pk_chatlog PRIMARY KEY (CHATID),
    CONSTRAINT fk_chatlog_receiver FOREIGN KEY (RECEIVERID) REFERENCES USERBASE(USERID),
    CONSTRAINT fk_chatlog_sender FOREIGN KEY (SENDERID) REFERENCES USERBASE(USERID)
);

INSERT ALL
    INTO CHATLOG VALUES (1, 101, 102, SYSDATE - 5, 'Hey, want to play later?')
    INTO CHATLOG VALUES (2, 102, 101, SYSDATE - 4, 'Sure, what game?')
    INTO CHATLOG VALUES (3, 103, 101, SYSDATE - 3, 'Nice profile picture!')
    INTO CHATLOG VALUES (4, 101, 103, SYSDATE - 3, 'Thanks!')
    INTO CHATLOG VALUES (5, 104, 102, SYSDATE - 2, 'Did you see the new update?')
    INTO CHATLOG VALUES (6, 102, 104, SYSDATE - 2, 'Yes, it looks amazing!')
    INTO CHATLOG VALUES (7, 105, 106, SYSDATE - 1, 'Can you help me with this level?')
    INTO CHATLOG VALUES (8, 106, 105, SYSDATE - 1, 'Of course, I''ll join now')
    INTO CHATLOG VALUES (9, 107, 108, SYSDATE, 'Great game yesterday')
    INTO CHATLOG VALUES (10, 108, 107, SYSDATE, 'Yeah, we should do it again')
    INTO CHATLOG VALUES (11, 109, 110, SYSDATE, 'Are you online?')
    INTO CHATLOG VALUES (12, 110, 109, SYSDATE, 'Just logged in')
    INTO CHATLOG VALUES (13, 101, 104, SYSDATE, 'Check out this new feature')
    INTO CHATLOG VALUES (14, 104, 101, SYSDATE, 'Looks cool!')
    INTO CHATLOG VALUES (15, 102, 103, SYSDATE, 'Happy birthday!')
SELECT * FROM dual;

CREATE TABLE FRIENDSLIST (
    USERID NUMBER(3),
    FRIENDID NUMBER(3),
    CONSTRAINT pk_friendslist PRIMARY KEY (USERID, FRIENDID),
    CONSTRAINT fk_friendslist_user FOREIGN KEY (USERID) REFERENCES USERBASE(USERID),
    CONSTRAINT fk_friendslist_friend FOREIGN KEY (FRIENDID) REFERENCES USERBASE(USERID)
);

INSERT ALL
    INTO FRIENDSLIST VALUES (101, 102)
    INTO FRIENDSLIST VALUES (101, 103)
    INTO FRIENDSLIST VALUES (102, 101)
    INTO FRIENDSLIST VALUES (102, 104)
    INTO FRIENDSLIST VALUES (103, 101)
    INTO FRIENDSLIST VALUES (103, 105)
    INTO FRIENDSLIST VALUES (104, 102)
    INTO FRIENDSLIST VALUES (104, 106)
    INTO FRIENDSLIST VALUES (105, 103)
    INTO FRIENDSLIST VALUES (105, 107)
    INTO FRIENDSLIST VALUES (106, 104)
    INTO FRIENDSLIST VALUES (106, 108)
    INTO FRIENDSLIST VALUES (107, 105)
    INTO FRIENDSLIST VALUES (107, 109)
    INTO FRIENDSLIST VALUES (108, 106)
SELECT * FROM dual;

CREATE TABLE WISHLIST (
    USERID NUMBER(3),
    PRODUCTCODE VARCHAR2(5),
    POSITION NUMBER(3),
    CONSTRAINT pk_wishlist PRIMARY KEY (USERID, PRODUCTCODE),
    CONSTRAINT fk_wishlist_user FOREIGN KEY (USERID) REFERENCES USERBASE(USERID),
    CONSTRAINT fk_wishlist_product FOREIGN KEY (PRODUCTCODE) REFERENCES PRODUCTLIST(PRODUCTCODE)
);

INSERT ALL
   INTO WISHLIST VALUES (101, 'GAME1', 1)
    INTO WISHLIST VALUES (101, 'GAME2', 2)
    INTO WISHLIST VALUES (102, 'GAME3', 1)
    INTO WISHLIST VALUES (102, 'GAME4', 2)
    INTO WISHLIST VALUES (103, 'GAME1', 1)
    INTO WISHLIST VALUES (103, 'GAME5', 2)
    INTO WISHLIST VALUES (104, 'GAME2', 1)
    INTO WISHLIST VALUES (104, 'GAME3', 2)
    INTO WISHLIST VALUES (105, 'GAME4', 1)
    INTO WISHLIST VALUES (105, 'GAME5', 2)
    INTO WISHLIST VALUES (106, 'GAME1', 1)
    INTO WISHLIST VALUES (106, 'GAME6', 2)
    INTO WISHLIST VALUES (107, 'GAME2', 1)
    INTO WISHLIST VALUES (107, 'GAME7', 2)
    INTO WISHLIST VALUES (108, 'GAME3', 1)
SELECT * FROM dual;

CREATE TABLE USERPROFILE (
    USERID NUMBER(3),
    IMAGEFILE VARCHAR2(250),
    DESCRIPTION VARCHAR2(250),
    CONSTRAINT pk_userprofile PRIMARY KEY (USERID),
    CONSTRAINT fk_userprofile_user FOREIGN KEY (USERID) REFERENCES USERBASE(USERID)
);

INSERT ALL
    INTO USERPROFILE VALUES (101, '/images/user101.jpg', 'Gaming enthusiast and streamer')
    INTO USERPROFILE VALUES (102, '/images/user102.png', 'Love RPG and strategy games')
    INTO USERPROFILE VALUES (103, '/images/user103.jpg', 'Competitive player')
    INTO USERPROFILE VALUES (104, '/images/user104.jpg', 'Game developer by day, gamer by night')
    INTO USERPROFILE VALUES (105, '/images/user105.png', 'Achievement hunter')
    INTO USERPROFILE VALUES (106, '/images/user106.jpg', 'Casual gamer looking for friends')
    INTO USERPROFILE VALUES (107, '/images/user107.jpg', 'Retro game collector')
    INTO USERPROFILE VALUES (108, '/images/user108.png', 'FPS specialist')
    INTO USERPROFILE VALUES (109, '/images/user109.jpg', 'Game reviewer')
    INTO USERPROFILE VALUES (110, '/images/user110.jpg', 'Just here for the community')
    INTO USERPROFILE VALUES (111, '/images/user111.jpg', 'VR gaming pioneer')
    INTO USERPROFILE VALUES (112, '/images/user112.jpg', 'Indie game supporter')
    INTO USERPROFILE VALUES (113, '/images/user113.png', 'Speedrunner')
    INTO USERPROFILE VALUES (114, '/images/user114.jpg', 'Game mod creator')
    INTO USERPROFILE VALUES (115, '/images/user115.jpg', 'Professional streamer')
SELECT * FROM dual;

CREATE TABLE SECURITYQUESTION (
    QUESTIONID NUMBER,
    USERID NUMBER(3),
    QUESTION VARCHAR2(250),
    ANSWER VARCHAR2(250),
    CONSTRAINT pk_securityquestion PRIMARY KEY (QUESTIONID),
    CONSTRAINT fk_securityquestion_user FOREIGN KEY (USERID) REFERENCES USERBASE(USERID)
);

INSERT ALL
    INTO SECURITYQUESTION VALUES (1, 101, 'What was your first pet''s name?', 'Max')
    INTO SECURITYQUESTION VALUES (2, 101, 'What city were you born in?', 'Boston')
    INTO SECURITYQUESTION VALUES (3, 102, 'What is your mother''s maiden name?', 'Smith')
    INTO SECURITYQUESTION VALUES (4, 103, 'What was your first car?', 'Honda Civic')
    INTO SECURITYQUESTION VALUES (5, 104, 'What elementary school did you attend?', 'Lincoln Elementary')
    INTO SECURITYQUESTION VALUES (6, 105, 'What is your favorite book?', 'The Hobbit')
    INTO SECURITYQUESTION VALUES (7, 106, 'What is your oldest sibling''s name?', 'Sarah')
    INTO SECURITYQUESTION VALUES (8, 107, 'What was your childhood nickname?', 'Ace')
    INTO SECURITYQUESTION VALUES (9, 108, 'What street did you grow up on?', 'Maple Street')
    INTO SECURITYQUESTION VALUES (10, 109, 'What is your favorite movie?', 'Inception')
    INTO SECURITYQUESTION VALUES (11, 110, 'What was the name of your first teacher?', 'Mrs. Johnson')
    INTO SECURITYQUESTION VALUES (12, 111, 'Where did you go on your first vacation?', 'Disney World')
    INTO SECURITYQUESTION VALUES (13, 112, 'What is your favorite food?', 'Pizza')
    INTO SECURITYQUESTION VALUES (14, 113, 'What is the name of your first boss?', 'Mike Thompson')
    INTO SECURITYQUESTION VALUES (15, 114, 'What is your dream job?', 'Game Developer')
SELECT * FROM dual;

CREATE TABLE COMMUNITYRULES (
    RULENUM NUMBER(3),
    TITLE VARCHAR2(250),
    DESCRIPTION VARCHAR2(250),
    SEVERITYPOINT NUMBER(4),
    CONSTRAINT pk_communityrules PRIMARY KEY (RULENUM)
);

INSERT ALL
    INTO COMMUNITYRULES VALUES (1, 'No Harassment', 'Treat all members with respect - no bullying or harassment', 10)
    INTO COMMUNITYRULES VALUES (2, 'No Hate Speech', 'Discriminatory language or content is strictly prohibited', 10)
    INTO COMMUNITYRULES VALUES (3, 'No Cheating', 'Using hacks or exploits in games is forbidden', 8)
    INTO COMMUNITYRULES VALUES (4, 'Respect Privacy', 'Do not share personal information of others', 7)
    INTO COMMUNITYRULES VALUES (5, 'No Spamming', 'Avoid excessive messages or advertising', 5)
    INTO COMMUNITYRULES VALUES (6, 'Appropriate Content', 'Keep all content family-friendly', 6)
    INTO COMMUNITYRULES VALUES (7, 'No Impersonation', 'Do not pretend to be staff or other users', 8)
    INTO COMMUNITYRULES VALUES (8, 'Follow Game Rules', 'Adhere to specific game server rules', 5)
    INTO COMMUNITYRULES VALUES (9, 'No Account Sharing', 'Do not share your account credentials', 4)
    INTO COMMUNITYRULES VALUES (10, 'Proper Language', 'Use appropriate language in all communications', 3)
    INTO COMMUNITYRULES VALUES (11, 'No Exploiting', 'Report bugs instead of exploiting them', 7)
    INTO COMMUNITYRULES VALUES (12, 'Respect Staff', 'Follow instructions from moderators and admins', 6)
    INTO COMMUNITYRULES VALUES (13, 'No Toxic Behavior', 'Maintain a positive gaming environment', 7)
    INTO COMMUNITYRULES VALUES (14, 'Proper Usernames', 'Usernames must be appropriate and not offensive', 4)
    INTO COMMUNITYRULES VALUES (15, 'No Scamming', 'Fraudulent activities are strictly prohibited', 10)
SELECT * FROM dual;

CREATE TABLE INFRACTIONS (
    INFRACTIONID NUMBER,
    USERID NUMBER(3),
    RULENUM NUMBER(3),
    DATEASSIGNED DATE,
    PENALTY VARCHAR2(250),
    CONSTRAINT pk_infractions PRIMARY KEY (INFRACTIONID),
    CONSTRAINT fk_infractions_user FOREIGN KEY (USERID) REFERENCES USERBASE(USERID),
    CONSTRAINT fk_infractions_rule FOREIGN KEY (RULENUM) REFERENCES COMMUNITYRULES(RULENUM)
);

INSERT ALL
    INTO INFRACTIONS VALUES (1, 115, 5, SYSDATE - 30, 'Warning')
    INTO INFRACTIONS VALUES (2, 114, 10, SYSDATE - 25, '24-hour chat ban')
    INTO INFRACTIONS VALUES (3, 113, 3, SYSDATE - 20, '7-day account suspension')
    INTO INFRACTIONS VALUES (4, 112, 1, SYSDATE - 18, 'Final warning')
    INTO INFRACTIONS VALUES (5, 111, 2, SYSDATE - 15, 'Permanent ban')
    INTO INFRACTIONS VALUES (6, 110, 4, SYSDATE - 12, 'Warning')
    INTO INFRACTIONS VALUES (7, 109, 6, SYSDATE - 10, 'Content removed')
    INTO INFRACTIONS VALUES (8, 108, 8, SYSDATE - 8, '3-day suspension')
    INTO INFRACTIONS VALUES (9, 107, 7, SYSDATE - 6, 'Account restricted')
    INTO INFRACTIONS VALUES (10, 106, 9, SYSDATE - 5, 'Warning')
    INTO INFRACTIONS VALUES (11, 105, 11, SYSDATE - 4, 'Temporary ban')
    INTO INFRACTIONS VALUES (12, 104, 12, SYSDATE - 3, 'Verbal warning')
    INTO INFRACTIONS VALUES (13, 103, 13, SYSDATE - 2, 'Chat restricted')
    INTO INFRACTIONS VALUES (14, 102, 14, SYSDATE - 1, 'Name change required')
    INTO INFRACTIONS VALUES (15, 101, 15, SYSDATE, 'Under investigation')
SELECT * FROM dual;

CREATE TABLE USERSUPPORT (
    TICKETID NUMBER,
    EMAIL VARCHAR2(250),
    ISSUE VARCHAR2(250),
    DATESUBMITTED DATE,
    DATEUPDATED DATE,
    STATUS VARCHAR2(250),
    CONSTRAINT pk_usersupport PRIMARY KEY (TICKETID)
);

INSERT ALL
    INTO USERSUPPORT VALUES (1, 'user101@email.com', 'Cannot login to account', SYSDATE - 7, SYSDATE - 6, 'CLOSED')
    INTO USERSUPPORT VALUES (2, 'user102@email.com', 'Payment not processed', SYSDATE - 6, SYSDATE - 5, 'CLOSED')
    INTO USERSUPPORT VALUES (3, 'user103@email.com', 'Game download stuck', SYSDATE - 5, SYSDATE - 4, 'CLOSED')
    INTO USERSUPPORT VALUES (4, 'user104@email.com', 'Friend request not working', SYSDATE - 4, SYSDATE - 3, 'IN PROGRESS')
    INTO USERSUPPORT VALUES (5, 'user105@email.com', 'Chat feature bug', SYSDATE - 3, SYSDATE - 2, 'IN PROGRESS')
    INTO USERSUPPORT VALUES (6, 'user106@email.com', 'Profile picture not updating', SYSDATE - 2, SYSDATE - 2, 'NEW')
    INTO USERSUPPORT VALUES (7, 'user107@email.com', 'Security question reset', SYSDATE - 2, SYSDATE - 1, 'IN PROGRESS')
    INTO USERSUPPORT VALUES (8, 'user108@email.com', 'Wishlist items missing', SYSDATE - 1, SYSDATE - 1, 'NEW')
    INTO USERSUPPORT VALUES (9, 'user109@email.com', 'Community guidelines question', SYSDATE - 1, SYSDATE, 'NEW')
    INTO USERSUPPORT VALUES (10, 'user110@email.com', 'Account hacked', SYSDATE, SYSDATE, 'NEW')
    INTO USERSUPPORT VALUES (11, 'user111@email.com', 'Refund request', SYSDATE - 8, SYSDATE - 7, 'CLOSED')
    INTO USERSUPPORT VALUES (12, 'user112@email.com', 'Two-factor authentication issue', SYSDATE - 3, SYSDATE - 2, 'IN PROGRESS')
    INTO USERSUPPORT VALUES (13, 'user113@email.com', 'Game purchase missing', SYSDATE - 2, SYSDATE - 1, 'IN PROGRESS')
    INTO USERSUPPORT VALUES (14, 'user114@email.com', 'Profile description not saving', SYSDATE - 1, SYSDATE - 1, 'NEW')
    INTO USERSUPPORT VALUES (15, 'user115@email.com', 'Infraction appeal', SYSDATE, SYSDATE, 'NEW')
SELECT * FROM dual;

CREATE VIEW UNIQUE_QUESTIONS_VIEW AS
SELECT DISTINCT QUESTION
FROM SECURITYQUESTION
ORDER BY QUESTION;

CREATE VIEW ACTIVE_SUPPORT_TICKETS_VIEW AS
SELECT TICKETID, EMAIL, ISSUE, DATEUPDATED
FROM USERSUPPORT
WHERE STATUS IN ('NEW', 'IN PROGRESS')
ORDER BY DATEUPDATED ASC;

COMMIT;
