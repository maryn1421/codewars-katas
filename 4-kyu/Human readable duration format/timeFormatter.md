Your task in order to complete this Kata is to write a function which formats a duration, given as a number of seconds, in a human-friendly way.

The function must accept a non-negative integer. If it is zero, it just returns "now". Otherwise, the duration is expressed as a combination of years, days, hours, minutes and seconds.

It is much easier to understand with an example:

TimeFormatter.formatDuration(62)   //returns "1 minute and 2 seconds"
TimeFormatter.formatDuration(3662) //returns "1 hour, 1 minute and 2 seconds"
For the purpose of this Kata, a year is 365 days and a day is 24 hours.

Note that spaces are important.

Detailed rules
The resulting expression is made of components like 4 seconds, 1 year, etc. In general, a positive integer and one of the valid units of time, separated by a space. The unit of time is used in plural if the integer is greater than 1.

The components are separated by a comma and a space (", "). Except the last component, which is separated by " and ", just like it would be written in English.

A more significant units of time will occur before than a least significant one. Therefore, 1 second and 1 year is not correct, but 1 year and 1 second is.

Different components have different unit of times. So there is not repeated units like in 5 seconds and 1 second.

A component will not appear at all if its value happens to be zero. Hence, 1 minute and 0 seconds is not valid, but it should be just 1 minute.

A unit of time must be used "as much as possible". It means that the function should not return 61 seconds, but 1 minute and 1 second instead. Formally, the duration specified by of a component must not be greater than any valid more significant unit of time.







#### my solution:


````java
 public static class TimeFormatter {
        public String formatDuration(int seconds) {
            if (seconds == 0) return "now";

            HashMap<String, Integer> resultMap = calculateFromSeconds(seconds);

            String result = getResultString(resultMap.get("seconds"), resultMap.get("years"), resultMap.get("days"), resultMap.get("hours"), resultMap.get("minutes"));
            List<String> elements = getResultListWithColons(result);
            return elements.stream().collect(Collectors.joining(" "));
        }


        private HashMap<String, Integer> calculateFromSeconds(int seconds) {
            int yearCalc = 365 * 24 * 60 * 60;
            int dayCalc = 24 * 60 * 60;
            int hourCalc = 60 * 60;
            int minuteCalc = 60;


            HashMap<String, Integer> results = new HashMap<>();

            int years = seconds / yearCalc;
            results.put("years", years);

            int sumDays = seconds - (years * yearCalc);
            int days =  sumDays / dayCalc;
            results.put("days", days);

            int sumHours = sumDays - (days * dayCalc);
            int hours = (sumHours / hourCalc);
            results.put("hours", hours);

            int sumMin = sumHours - (hours * hourCalc);
            int minutes =  (sumMin / minuteCalc);
            results.put("minutes", minutes);

            seconds = sumMin - (minutes * minuteCalc);
            results.put("seconds", seconds);

            return results;
        }


        private List<String> getResultListWithColons(String result) {
            List<String> elementList = Arrays.asList(result.split(" "));

            if (elementList.size() > 2) {
                elementList.set(elementList.size() - 2, "and " + elementList.get(elementList.size() - 2));
            }

            for (int i = 1; i <= elementList.size() - 4; i++) {
                if (i % 2 == 0) {
                    String current = elementList.get(i - 1);
                    elementList.set(i - 1, current + ",");
                }
            }
            return elementList;
        }

        private String getResultString(int seconds, int years, int days, int hours, int minutes) {
            String result = "";
            result += years > 1 ? years + " years " : years > 0 ? years + " year " : "";
            result += days > 1 ? days + " days " : days > 0 ? days + " day " : "";
            result += hours > 1 ? hours + " hours " : hours > 0 ? hours + " hour " : "";
            result += minutes > 1 ? minutes + " minutes " : minutes > 0 ? minutes + " minute " : "";
            result += seconds > 1 ? seconds + " seconds " : seconds > 0 ? seconds + " second " : "";
            return result.trim();
        }
    }

````