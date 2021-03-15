<template>
  <div class="container d-lg-flex flex-wrap">
    <video-box v-for="(video, i) in videos" :key="i" :source="video" />
  </div>
</template>

<script>
import VideoBox from "~/components/VideoBox.vue";

export default {
  components: {
    VideoBox,
  },
  data() {
    return {
      videos: [
        {
          id: 1,
          title: "It's pronounced GIF.",
          channel: "Tom Scott",
          channelId: 1,
          length: "10:24",
          views: "2.7M",
          dateAdded: "1 years ago",
        },
        {
          id: 2,
          title: "This Video Has 2893567 Views.",
          channel: "Tom Scott",
          channelId: 1,
          length: "9:23",
          views: "2.8M",
          dateAdded: "6 months ago",
        },
        {
          id: 0,
          title: "Why you NEED math for programming..",
          channel: "Joma Tech",
          channelId: 0,
          length: "6:35",
          views: "875K",
          dateAdded: "2 years ago",
        },
        {
          id: 3,
          title: "What happened if the world turned to Gold?",
          channel: "Kurzgesagt – In a Nutshell",
          channelId: 6,
          length: "24:12",
          views: "896K",
          dateAdded: "2 weeks ago",
        },
        {
          id: 4,
          title: "How Hot Can It Get?",
          channel: "Vsauce",
          channelId: 2,
          length: "17:21",
          views: "14M",
          dateAdded: "3 years ago",
        },
        {
          id: 5,
          title: "The Banach – Tarski Paradox",
          channel: "Vsauce",
          channelId: 2,
          length: "24:13",
          views: "32M",
          dateAdded: "5 years ago",
        },
        {
          id: 7,
          title: "Why You Can Spot Bad Green Screen",
          channel: "Tom Scott",
          channelId: 1,
          length: "7:12",
          views: "4.3M",
          dateAdded: "3 years ago",
        },
        {
          id: 8,
          title: "Why Microsoft Word is the best IDE for programming",
          channel: "Joma Tech",
          channelId: 0,
          length: "9:25",
          views: "725K",
          dateAdded: "4 months ago",
        },
        {
          id: 9,
          title: "VSCode Tinder",
          channel: "Ben Awad",
          channelId: 5,
          length: "10:29",
          views: "546K",
          dateAdded: "3 months ago",
        },
        {
          id: 10,
          title: "ben awad bashing angular for 5 minutes straight",
          channel: "TinyTuba",
          channelId: 3,
          length: "5:12",
          views: "152K",
          dateAdded: "1 year ago",
        },
        {
          id: 11,
          title: 'Why Some "Remastered" Music Videos Look Awful',
          channel: "Tom Scott",
          channelId: 1,
          length: "9:54",
          views: "2.3M",
          dateAdded: "2 years ago",
        },
        {
          id: 12,
          title: "Ink Cartirdges Are A Scam",
          channel: "AustinMcConnell ",
          channelId: 7,
          length: "12:52",
          views: "8.5M",
          dateAdded: "2 years ago",
        },
        {
          id: 13,
          title: "I Can't Show You How Pink This Pink Is",
          channel: "Tom Scott",
          channelId: 1,
          length: "6:51",
          views: "7.5M",
          dateAdded: "3 year ago",
        },
        {
          id: 14,
          title:
            "What's The Longest Word You Can Write With Seven-Segment Displays?",
          channel: "Tom Scott",
          channelId: 1,
          length: "8:55",
          views: "2.8M",
          dateAdded: "3 year ago",
        },
        {
          id: 6,
          title: "The Museum of Failure",
          channel: "Tom Scott",
          channelId: 1,
          length: "2:23",
          views: "1.7M",
          dateAdded: "4 years ago",
        },
        {
          id: 15,
          title: "Why Dark Video Is A Terrible Blocky Mess",
          channel: "Tom Scott",
          channelId: 1,
          length: "6:15",
          views: "2.8M",
          dateAdded: "6 years ago",
        },
        {
          id: 16,
          title: "So You've Learned To Teleport",
          channel: "Tom Scott",
          channelId: 1,
          length: "3:55",
          views: "2.9M",
          dateAdded: "4 years ago",
        },
        {
          id: 17,
          title: "Elia: The World's Most Frustrating Work of Art",
          channel: "Tom Scott",
          channelId: 1,
          length: "2:31",
          views: "2.8M",
          dateAdded: "4 years ago",
        },
      ],
    };
  },
};
</script>
