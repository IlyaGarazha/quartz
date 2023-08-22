
/usr/share/plasma/plasmoids/org.kde.plasma.digitalclock/contents/ui/DigitalClock.qml
code:
```javascript
if (main.showDate) {
            dateLabel.text = Qt.formatDate(main.getCurrentTime(), "dd.MM");
        } else {
            // clear it so it doesn't take space in the layout
            dateLabel.text = "";
        }

```
