## Improve your Design Handoff + free Figma Template

## **Intro**

To build an awesome and successful digital product you need to do a lot of things. Things like planning, market research, build a prototype, design it, code it, ship it etc... To go through this whole process you need to go through lots of handoffs and team communications. One of the more painful handoffs is the Design-to-Development Handoff.

This happens because usually, the design and development happen in 2 separate teams. The design team handles creating the design system, user interfaces, graphics and visuals. The dev team turn the design deliverables into a functional product.

## So what is Design-to-Development Handoff?

Design handoff is when the design team hands their deliverables over to the dev team. The dev team then begins with the implementation. This process could turn into a nightmare if there are no standards implemented. Since the product's quality is at stake, it's a good idea to enable a good collaboration between the two teams.

This is not rocket science. There are tons of tools and platforms available that ease out the design handoff. To maintain a smooth design handoff, both designers and developers must take place into the process. Here are some tips for the designers and developers on how to improve the design handoff.

## Tips for designers

1.  Be interested in the frameworks. Talk with the developers on what framework they plan to use and read about it. Are they using [Bootstrap](https://getbootstrap.com/)? Or [Tailwind CSS](https://tailwindcss.com/)? Get to know it and its possible limitations. Knowing the possibilities and limitations will help you create more suitable design elements.
2.  After studying the framework, try to use the UI elements that come with it. Map the framework's color palette, spacing, typography settings and everything that you can.
3.  Follow the design trends for the platform that you're designing. For example, if you're designing an iOS app, don't set the tab bar height by random. There are Design Guidelines for both [iOS](https://developer.apple.com/design/human-interface-guidelines/) and [Android](https://developer.android.com/design) available, so make sure you read them. The development team will thank you for it!
4.  Use a modern tool for UI Design. It's time to ditch Photoshop. If you want to stay in the Adobe ecosystem, then check out [Adobe XD](https://www.adobe.com/products/xd.html). If not, I recommend to take a look at [Figma](https://figma.com/).

## Tips for developers

1.  Teach your designers about the framework you plan to use. But also, let them teach you about the design tools they plan to use. Learn how to use Figma, or Adobe XD, or Sketch, or whatever the design team uses. You will be using that tool to view the design and build the product, so make sure you study it.
2.  Design systems aren't only for the designers. Talk with the designers and create the design system in code. If you're developing a website, create a **theme.config.js** file and set up the design system there. Add the color palette, the spacing, the typography system. Try not to forget any elements from the design system. The js file should be simple. Here's something to get you started:


```javascript
module.exports = {
   colors: {
      ...
   },
   fontFamily: {
      ...
   },
   margin: {
      ...
   },
   padding: {
      ...
   }
}
``` 


1.  After setting up the design system, don't use values outside of it. If the margins in the design systems are 18px and 20px, never use 19px anywhere! Import your theme file and use only the things defined in it.
2.  When viewing the design system, don't be superficial! Every little detail counts. If the designer set the background to `#121212`, don't see it as black and set it to `#000000` without checking. Check everything. Check the color, the font size, the line height, the border radius. You might think otherwise, but it's the little things that makes the design feel complete.

## Tips for both teams

1.  Communicate. Leave nothing to chance. If you're not sure about something, communicate it with your colleagues.
2.  Leave notes. The modern design tools like Figma and Adobe XD have Comments built in. Both teams can use the Comments system to ask questions and add explanations.
3.  Review your work. After finishing a feature, make sure to review it. I'm talking about **both** teams. Make sure the code is clean, and the design implementation is correct.

## Conclusion

Working in teams is not always easy. But, it shouldn't be a nightmare too. Be smart about the tools you're using. Also, be smart about the communication. When the developers and designers are in total sync, amazing things can happen.

## Free Figma Template
Click [here](https://www.figma.com/file/Gp06ea38Z2OBiMoXh8a8B1/Design-Handoff-Tailwind-CSS?node-id=0%3A1) to get the free Figma template.