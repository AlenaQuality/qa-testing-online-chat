## Checklist for testing online chats:

1. **Functional testing.**  
- [ ] Check chat availability in the web app. 

At this step, apply the test design technique of partitioning into equivalence classes: authorized (chat is available) and unauthorized user (chat is not available).

- [ ] Check that the WebSocket connection is successfully established (receiving status 101, correct request headers)  
- [ ] Sending valid text messages  
- [ ] Check that the server correctly processes messages containing special characters and/or emojis  
- [ ] Make sure messages with special characters and emojis are displayed correctly in chat  
- [ ] Check the display of different types of emoji (Unicode, emoji emoticons)  
- [ ] Make sure that when you send links they are converted into clickable ones  
- [ ] Check that different types of links are processed (http, https, ftp, internal links)  
- [ ] Check error handling when following incorrect or broken links  
- [ ] Check sending empty messages/containing single spaces  
- [ ] Check sending messages with line breaks.

Boundary Value Technique: check Minimum and Maximum Text Length.

- [ ] Editing text messages. Make sure that the text can be edited, after editing the message is updated for both the user and the manager  
- [ ] Test editing on behalf of different users (user, manager)  
- [ ] Check edits of messages of different lengths, including length limits  
- [ ] Check the editing of the message while the second chat participant is reading it  
- [ ] Make sure edits can be undone  
- [ ] Check the delete function (depending on requirements).

When performing these tests, it is useful to use a paired testing technique. It will cover different message editing scenarios.

- [ ] Check for an error when you try to send a text message that exceeds the character limit. Verify that the message is not being sent and that the server returns an error correctly  
- [ ] Verify that attachments are sent with acceptable formats and sizes.

Technique: breakdown by equivalence classes (acceptable and unacceptable attachment formats according to the requirements) and limit values ​​(minimum and maximum attachment size/number of attachments in one message).

- [ ] Check the attachment preview feature  
- [ ] Check the function of downloading multiple files at the same time (different sizes and formats)  
- [ ] Check the processing of attachments with the same file names  
- [ ] Check for an error when sending an invalid file format  
- [ ] Check for an error when sending a file larger than 10MB  
- [ ] Check your read status. Make sure that synchronization works without delays and the read status is correctly displayed in the interface  
- [ ] Check the available functions: adding an "important" flag/adding a message to favorites, etc.

Use the state testing technique: message sent, delivered, read, marked. Or you can use the Decision Table to check all possible combinations, adding checks: message with a flag, without a flag, after removing the flag.

- [ ] Verify that message history is saved and accessible to the user and manager  
- [ ] Make sure message history is not lost after page reload/logout or browser closing  
- [ ] Check the message history search function  
- [ ] Check the speed of loading chat and sending messages  
- [ ] Simulate a connection break and test the WebSocket connection to reconnect  
- [ ] Check that server connection errors are handled correctly  
- [ ] Check the correct error handling when sending messages (for example, behavior when the file size is exceeded or is invalid.  
2. **Non-functional testing.**

Let's divide them into subtypes of testing:

1. **Usability testing**  
- [ ] Check chat opening/closing  
- [ ] Check that all types of messages are displayed correctly. Make sure very long and very short messages are displayed correctly  
- [ ] Make sure attachments are loaded in responsive format  
- [ ] Check the convenience and intuitiveness of the interface  
- [ ] Check that notifications about new messages are working correctly  
- [ ] Make sure that error descriptions (for example, file size exceeded) are present and that they are clear to the user.  
      2. **Compatibility testing**  
- [ ] Test the chat functionality in different browsers (when choosing browsers, be guided by business requirements)  
- [ ] Test the chat on different devices (PCs, smartphones, tablets).  
      3. **Localization testing**  
- [ ] Check that the chat interface and messages are displayed correctly in different languages. Use the technique of partitioning by equivalent values.  
- [ ] Make sure that the date and time match the user's locale.  
      4. **Security testing**  
- [ ] Make sure chats are only accessible to authorized users  
- [ ] Check resistance to SQL injections in messages  
- [ ] Check rate limiting to prevent spam  
- [ ] Check that you are using a secure connection (wss://) for data transfer.  
      5. **Reliability testing**  
- [ ] Simulate a disconnection and check that the chat is restored correctly after the disconnection  
- [ ] Make sure that all message history is saved after the connection is disconnected and the page is refreshed  
- [ ] Check scenarios for saving and resending unsent messages after connection is restored  
      6. **Load testing**  
- [ ] Check processing of a large number of messages (for example 100+ in a row)  
- [ ] Check the handling of sending and receiving a large number of attachments with a maximum size  
- [ ] Check chat load and message history if there are a lot of entries.  
      7. **Stress testing**  
- [ ] Check system behavior under load conditions (e.g. 10,000 simultaneous users).

